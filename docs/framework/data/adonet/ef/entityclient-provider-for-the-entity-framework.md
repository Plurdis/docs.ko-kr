---
title: Entity Framework용 EntityClient 공급자
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: bf3bf6fe0d0013b3e5b05ec697ad4f6a57459a6f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Entity Framework용 EntityClient 공급자
EntityClient 공급자는 Entity Framework 응용 프로그램에서 개념적 모델에 설명된 데이터에 액세스하는 데 사용하는 데이터 공급자입니다. 개념적 모델에 대 한 정보를 참조 하십시오. [모델링 및 매핑](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)합니다. EntityClient는 다른 .NET Framework 데이터 공급자를 사용하여 데이터 소스에 액세스합니다. 예를 들어, EntityClient는 SQL Server 데이터베이스에 액세스할 때 .NET Framework Data Provider for SQL Server(SqlClient)를 사용합니다. SqlClient 공급자에 대 한 정보를 참조 하십시오. [Entity Framework 용 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)합니다. EntityClient 공급자는 <xref:System.Data.EntityClient> 네임스페이스에 구현되어 있습니다.  
  
## <a name="managing-connections"></a>연결 관리  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]는 기본 데이터 공급자 및 관계형 데이터베이스에 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]을 제공하는 방법으로 저장소별 <xref:System.Data.EntityClient.EntityConnection> 데이터 공급자를 기반으로 빌드됩니다. 생성 하는 <xref:System.Data.EntityClient.EntityConnection> 개체를 필요한 모델 및 매핑 및 저장소별 데이터 공급자 이름 및 연결 문자열을 포함 하는 메타 데이터 집합을 참조 해야 합니다. 이후에 <xref:System.Data.EntityClient.EntityConnection> 는 장소 엔터티에 개념적 모델에서 생성 된 클래스를 통해 액세스할 수 있습니다.  
  
 app.config 파일에서 연결 문자열을 지정할 수 있습니다.  
  
 <xref:System.Data.EntityClient>는 <xref:System.Data.EntityClient.EntityConnectionStringBuilder> 클래스도 포함합니다. 개발자는 이 클래스를 사용하여 프로그래밍 방식으로 올바른 구문의 연결 문자열을 만들고 이 클래스의 속성과 메서드를 사용하여 기존 연결 문자열의 구문을 분석한 다음 다시 빌드할 수 있습니다. 자세한 내용은 참조 [하는 방법: EntityConnection 연결 문자열 작성](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)합니다.  
  
## <a name="creating-queries"></a>쿼리 작성  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 언어는 개념적 엔터티 스키마와 직접 통신 하며 상속 및 관계와 같은 엔터티 데이터 모델 개념을 지원 하는 SQL의 저장소에 독립적인 언어입니다. <xref:System.Data.EntityClient.EntityCommand> 클래스는 엔터티 모델에 대해 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 명령을 실행하는 데 사용됩니다. <xref:System.Data.EntityClient.EntityCommand> 개체를 생성할 때는 저장 프로시저 이름이나 쿼리 텍스트를 지정할 수 있습니다. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]는 저장소별 데이터 공급자와 함께 작업하여 일반 [!INCLUDE[esql](../../../../../includes/esql-md.md)]을 저장소별 쿼리로 변환합니다. 쓰기에 대 한 자세한 내용은 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 쿼리 참조 [Entity SQL 언어](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)합니다.  
  
 다음 예제에서는 <xref:System.Data.EntityClient.EntityCommand> 할당 및 개체는 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 쿼리 텍스트를 해당 <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> 속성입니다. 이 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 쿼리는 개념적 모델에서 목록 가격으로 주문한 제품을 요청 합니다. 다음 코드에는 저장소 모델에 대한 정보가 없습니다.  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"` `SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## <a name="executing-queries"></a>쿼리 실행  
 쿼리를 실행하면 쿼리에 대한 구문 분석이 수행되고 정식 명령 트리로 변환됩니다. 이후 모든 처리는 정식 명령 트리에서 수행됩니다. 명령 트리는 <xref:System.Data.EntityClient>와 기본 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 데이터 공급자(예: <xref:System.Data.SqlClient>) 간의 통신 수단입니다.  
  
 <xref:System.Data.EntityClient.EntityDataReader>는 개념적 모델에 대한 <xref:System.Data.EntityClient.EntityCommand> 실행 결과를 노출합니다. <xref:System.Data.EntityClient.EntityDataReader>를 반환하는 명령을 실행하려면 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>를 호출합니다. <xref:System.Data.EntityClient.EntityDataReader>는 결과를 다양한 구조로 보여 주는 <xref:System.Data.IExtendedDataRecord>를 구현합니다.  
  
## <a name="managing-transactions"></a>트랜잭션 관리  
 Entity Framework에서는 자동 및 명시적으로 트랜잭션을 사용할 수 있습니다. 자동 트랜잭션에서는 <xref:System.Transactions> 네임스페이스가 사용되고, 명시적 트랜잭션에서는 <xref:System.Data.EntityClient.EntityTransaction> 클래스가 사용됩니다.  
  
 즉, 개념적 모델을 통해 노출 되는 데이터를 업데이트 하려면 참조 [하는 방법: Entity Framework에서 트랜잭션을 관리할](http://msdn.microsoft.com/library/4a55eb7f-f826-4a48-9df1-aebe2352ebef)합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [방법: EntityConnection 연결 문자열 작성](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [방법: PrimitiveType 결과를 반환하는 쿼리 실행](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [방법: StructuralType 결과를 반환하는 쿼리 실행](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [방법: RefType 결과를 반환하는 쿼리 실행](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [방법: 복합 형식을 반환하는 쿼리 실행](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [방법: 중첩된 컬렉션을 반환하는 쿼리 실행](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [방법: EntityCommand를 사용하여 매개 변수가 있는 Entity SQL 쿼리 실행](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [방법: EntityCommand를 사용하여 매개 변수가 있는 저장 프로시저 실행](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [방법: 다형 쿼리 실행](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [방법: Navigate 연산자로 관계 탐색](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>참고 항목  
 [연결 및 트랜잭션 관리](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)  
 [언어 참조](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
