---
title: "정적으로 컴파일된 쿼리(LINQ to XML)(C#) | Microsoft 문서"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 10e4df75be88dc5609e0ca15666042a0354824bc
ms.lasthandoff: 03/13/2017


---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>정적으로 컴파일된 쿼리(LINQ to XML)(C#)
<xref:System.Xml.XmlDocument>와는 달리 LINQ to XML의 가장 큰 성능 이점 중 하나는 LINQ to XML의 쿼리가 정적으로 컴파일된다는 점입니다. 반면 XPath 쿼리는 런타임에 해석되어야 합니다. 이 기능은 LINQ to XML에 기본 제공되므로 이를 활용하기 위해 별도의 단계를 수행할 필요는 없습니다. 그러나 이 두 가지 기술 중 하나를 선택해야 하는 경우를 위해 그 차이를 알고 있는 것이 좋습니다. 이 항목에서는 그 차이에 대해 설명합니다.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>정적으로 컴파일된 쿼리와 XPath  
 다음 예제에서는 지정된 이름을 가진 하위 요소와 지정된 값을 가진 특성이 포함된 하위 요소를 가져오는 방법을 보여 줍니다.  
  
 다음은 이에 해당하는 XPath 식입니다.  
  
```  
//Address[@Type='Shipping']  
```  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 이 예제의 쿼리 식은 메서드 기반 쿼리 구문에 대한 컴파일러로 다시 작성되었습니다. 메서드 기반 쿼리 구문으로 작성된 다음 예제는 이전 쿼리에서와 같은 결과를 생성합니다.  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <xref:System.Linq.Enumerable.Where%2A> 메서드는 확장 메서드입니다. 자세한 내용은 [확장 메서드](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)를 참조하세요. <xref:System.Linq.Enumerable.Where%2A>는 확장 메서드이므로 위 쿼리는 다음과 같이 작성된 것처럼 컴파일됩니다.  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 이 예제의 결과는 위의 두 예제의 결과와 정확히 동일합니다. 이를 통해 쿼리가 정적으로 연결된 메서드 호출로 효과적으로 컴파일되었음을 알 수 있습니다. 이 예제에서는 반복기의 지연된 실행 의미 체계를 결합하여 성능을 향상합니다. 반복기의 지연된 실행 의미 체계에 대한 자세한 내용은 [LINQ to XML에서 지연 실행 및 지연 계산(C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)을 참조하세요.  
  
> [!NOTE]
>  이러한 예제는 컴파일러에서 작성할 수 있는 대표적인 코드 예제입니다. 실제 구현은 이러한 예제와 약간 다를 수 있으나 성능은 이러한 예제와 같거나 매우 유사할 것입니다.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>XmlDocument를 사용하여 XPath 식 실행  
 다음 예제에서는 <xref:System.Xml.XmlDocument>를 사용하여 위의 예제와 같은 결과를 제공합니다.  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 이 쿼리에서는 LINQ to XML을 사용하는 예제와 같은 결과를 반환합니다. LINQ to XML에서는 출력되는 XML을 들여쓰지만 <xref:System.Xml.XmlDocument>는 들여쓰지 않는다는 점만 다릅니다.  
  
 그러나 <xref:System.Xml.XmlNode.SelectNodes%2A> 메서드는 호출될 때마다 내부적으로 다음을 수행해야 하므로 <xref:System.Xml.XmlDocument>는 일반적으로 LINQ to XML과 같이 효과적으로 수행되지 않습니다.  
  
-   XPath 식이 포함된 문자열을 구문 분석하여 문자열을 토큰으로 나눕니다.  
  
-   XPath 식이 올바른지 확인하기 위해 토큰의 유효성을 검사합니다.  
  
-   식을 내부 식 트리로 변환합니다.  
  
-   노드를 반복하여 식 계산 결과를 기준으로 결과 집합에 맞는 노드를 선택합니다.  
  
 이는 이에 해당하는 LINQ to XML 쿼리에서 수행하는 작업보다 훨씬 많습니다. 구체적인 성능 차이는 쿼리 형식에 따라 다르지만 일반 LINQ to XML 쿼리의 경우 작업을 덜 수행하므로 <xref:System.Xml.XmlDocument>를 사용하여 XPath 식을 계산하는 것보다 성능이 더 좋습니다.  
  
## <a name="see-also"></a>참고 항목  
 [성능(LINQ to XML)(C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)