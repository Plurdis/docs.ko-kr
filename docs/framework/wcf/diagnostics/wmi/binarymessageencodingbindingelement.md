---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 03a33f01fe6b6f75e81749c96c31770009350b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement
BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>구문  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>메서드  
 BinaryMessageEncodingBindingElement 클래스는 메서드를 정의하지 않습니다.  
  
## <a name="properties"></a>속성  
 BinaryMessageEncodingBindingElement 클래스에는 다음과 같은 속성이 있습니다.  
  
## <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 데이터 형식: sint32  
  
 액세스 형식: 읽기 전용  
  
 새 판독기를 할당하지 않고 동시에 읽을 수 있는 메시지 수를 정의하는 정수입니다.  
  
## <a name="maxsessionsize"></a>MaxSessionSize  
 데이터 형식: sint32  
  
 액세스 형식: 읽기 전용  
  
 인코딩에 사용되는 버퍼의 크기(바이트)를 지정하는 값입니다.  
  
## <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 데이터 형식: sint32  
  
 액세스 형식: 읽기 전용  
  
 새 작성기를 할당하지 않고 동시에 보낼 수 있는 메시지 수를 정의하는 정수입니다.  
  
## <a name="readerquotas"></a>ReaderQuotas  
 데이터 형식: XmlDictionaryReaderQuotas  
  
 액세스 형식: 읽기 전용  
  
 판독기의 할당량입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|MOF|Servicemodel.mof에 선언되어 있습니다.|  
|---------|-----------------------------------|  
|네임스페이스|root\ServiceModel에 정의되어 있습니다.|  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
