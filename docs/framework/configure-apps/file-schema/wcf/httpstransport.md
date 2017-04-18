---
title: "&lt;httpsTransport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;httpsTransport&gt;
사용자 지정 바인딩의 SOAP 메시지 전송을 위한 HTTP 전송을 지정합니다.  
  
## 구문  
  
```  
  
<httpsTransport  
    allowCookies=Boolean"  
    authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"  
    bypassProxyOnLocal=Boolean"  
    hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
    manualAddressing="Boolean"  
    maxBufferPoolSize="Integer"  
    maxBufferSize="Integer"  
    maxReceivedMessageSize="Integer"  
    proxyAddress="Uri"  
    proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"        realm="String"  
    requireClientCertificate=Boolean"  
    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
        unsafeConnectionNtlmAuthentication="Boolean"  
....useDefaultWebProxy="Boolean"  
/>  
```  
  
## 특성 및 요소  
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### 특성  
  
|특성|설명|  
|--------|--------|  
|allowCookies|클라이언트가 쿠키를 수락하고 이를 앞으로의 요청에서 전파할지 여부를 지정하는 부울 값입니다.  기본값은 `false`입니다.<br /><br /> 쿠키를 사용하는 ASMX 웹 서비스와 상호 작용할 때 이 특성을 사용할 수 있습니다.  그러면 서버에서 반환된 쿠키가 해당 서비스에 대한 이후의 모든 클라이언트 요청에 자동으로 복사되도록 할 수 있습니다.|  
|authenticationScheme|HTTP 수신기가 처리하는 클라이언트 요청을 인증하는 데 사용되는 프로토콜을 지정합니다.  유효한 값은 다음과 같습니다.<br /><br /> -   Digest: 다이제스트 인증을 지정합니다.<br />-   Negotiate: 클라이언트와 협상하여 인증 체계를 결정합니다.  클라이언트와 서버 모두 Kerberos를 지원하면 이 인증 체계가 사용되고, 그렇지 않으면 NTLM이 사용됩니다.<br />-   Ntlm: NTLM 인증을 지정합니다.<br />-   Basic: 기본 인증을 지정합니다.<br />-   Anonymous: 익명 인증을 지정합니다.<br /><br /> 기본값은 Anonymous입니다.  이 특성은 <xref:System.Net.AuthenticationSchemes> 형식입니다.  이 특성은 한 번만 설정할 수 있습니다.|  
|bypassProxyOnLocal|로컬 주소에 대해 프록시 서버를 사용하지 않을 것인지 여부를 나타내는 부울 값입니다.  기본값은 `false`입니다.<br /><br /> 로컬 주소는 로컬 LAN 또는 인트라넷에 있는 주소입니다.<br /><br /> 서비스 주소가 http:\/\/localhost로 시작되는 경우 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]은 항상 프록시를 무시합니다.<br /><br /> 클라이언트가 동일한 시스템의 서비스와 통신할 때 프록시를 통하게 하려면 localhost 대신 호스트 이름을 사용해야 합니다.|  
|hostnameComparisonMode|URI 구문 분석에 사용되는 HTTP 호스트 이름 비교 모드를 지정합니다.  유효한 값은 다음과 같습니다.<br /><br /> -   StrongWildcard: \("\+"\)는 지정한 스키마, 포트 및 상대 URI의 컨텍스트에서 일치하는 모든 호스트 이름을 검색합니다.<br />-   Exact: 와일드카드 없음<br />-   WeakWildcard: \("\*"\)는 지정한 체계, 포트 및 상대 URI의 컨텍스트에서 또는 강력한 와일드카드 메커니즘을 통해 명시적으로 일치하지 않는 가능한 모든 호스트 이름을 검색합니다.<br /><br /> 기본값은 StrongWildcard입니다.  이 특성은 <xref:System.ServiceModel.HostnameComparisonMode> 형식입니다.|  
|manualAddressing|사용자가 메시지 주소 지정을 제어할 수 있도록 하는 부울 값입니다.  이 속성은 여러 대상 중 어느 대상으로부터 메시지를 받을 것인지를 응용 프로그램에서 결정하는 라우터 시나리오에서 주로 사용됩니다.<br /><br /> 이 속성이`true`로 설정되면 채널에서는 메시지에 이미 주소가 지정되었다고 가정하여 더 이상 정보를 추가하지 않습니다.  그러면 사용자는 모든 메시지의 주소를 개별적으로 지정할 수 있습니다.<br /><br /> `false`로 설정되면 기본 WCF\(Windows Communication Foundation\) 주소 지정 메커니즘이 모든 메시지에 대한 주소를 자동으로 만듭니다.<br /><br /> 기본값은 `false`입니다.|  
|maxBufferPoolSize|버퍼 풀의 최대 크기를 지정하는 양의 정수입니다.  기본값은 524288입니다.<br /><br /> WCF의 많은 부분에서 버퍼를 사용합니다.  버퍼를 사용할 때마다 만들고 삭제하면 비용이 많이 들며, 버퍼에 대한 가비지 수집 역시 비용이 많이 듭니다.  버퍼 풀이 있으면 이 풀로부터 버퍼를 가져와 사용한 다음 다시 풀로 반환할 수 있습니다.  따라서 버퍼를 만들고 삭제하는 데 오버헤드를 피할 수 있습니다.|  
|maxBufferSize|버퍼의 최대 크기를 지정하는 양의 정수입니다.  기본값은 524288입니다.|  
|maxReceivedMessageSize|받을 수 있는 허용되는 최대 메시지 크기\(바이트\)를 지정하는 양의 정수입니다.  기본값은 65536입니다.|  
|proxyAddress|HTTP 프록시의 주소를 지정하는 URI입니다.  `useSystemWebProxy`가 `true`일 경우 이 설정은 `null`이어야 합니다.  기본값은 `null`입니다.|  
|proxyAuthenticationScheme|HTTP 프록시가 처리하는 클라이언트 요청을 인증하는 데 사용되는 프로토콜을 지정합니다.  유효한 값은 다음과 같습니다.<br /><br /> -   None: 인증이 수행되지 않습니다.<br />-   Digest: 다이제스트 인증을 지정합니다.<br />-   Negotiate: 클라이언트와 협상하여 인증 체계를 결정합니다.  클라이언트와 서버 모두 Kerberos를 지원하면 이 인증 체계가 사용되고, 그렇지 않으면 NTLM이 사용됩니다.<br />-   Ntlm: NTLM 인증을 지정합니다.<br />-   Basic: 기본 인증을 지정합니다.<br />-   Anonymous: 익명 인증을 지정합니다.<br />-   IntegratedWindowsAuthentication: Windows 인증을 지정합니다.<br /><br /> 기본값은 Anonymous입니다.  이 특성은 <xref:System.Net.AuthenticationSchemes> 형식입니다.|  
|realm|프록시\/서버에서 사용할 영역을 지정하는 문자열입니다.  기본값은 빈 문자열입니다.<br /><br /> 서버에서는 보호되는 리소스를 분할할 때 영역을 사용합니다.  각 파티션에는 자체 인증 체계 및\/또는 권한 부여 데이터베이스가 있을 수 있습니다.  영역은 기본 및 다이제스트 인증에만 사용됩니다.  클라이언트가 성공적으로 인증되면 이 인증은 지정된 영역의 모든 리소스에 대해 유효합니다.  영역에 대한 자세한 내용은 http:\/\/www.ietf.org의 RFC 2617을 참조하세요.|  
|requireClientCertificate|클라이언트가 HTTPS 핸드셰이크의 일부로 클라이언트 인증서를 제공할 것을 서버에서 요구하는지 여부를 지정하는 부울 값입니다.  기본값은 `false`입니다.|  
|transferMode|메시지가 버퍼링되거나 스트리밍되는지 또는 요청이나 응답인지를 지정합니다.  유효한 값은 다음과 같습니다.<br /><br /> -   Buffered: 요청 및 응답 메시지가 버퍼링됩니다.<br />-   Streamed: 요청 및 응답 메시지가 스트리밍됩니다.<br />-   StreamedRequest: 요청 메시지는 스트리밍되고 응답 메시지는 버퍼링됩니다.<br />-   StreamedResponse: 요청 메시지는 버퍼링되고 응답 메시지는 스트리밍됩니다.<br /><br /> 기본값은 Buffered입니다.  이 특성은 <xref:System.ServiceModel.TransferMode> 형식입니다.|  
|unsafeConnectionNtlmAuthentication|서버에서 안전하지 않은 연결 공유를 사용할 수 있는지 여부를 지정하는 부울 값입니다.  기본값은 `false`입니다.  사용할 경우 각 TCP 연결에서 NTLM 인증이 한 번씩 수행됩니다.|  
|useDefaultWebProxy|사용자별 설정이 아닌 시스템 수준의 프록시 설정을 사용할지 여부를 지정하는 부울 값입니다.  기본값은 `true`입니다.|  
  
### 자식 요소  
 없음  
  
### 부모 요소  
  
|요소|설명|  
|--------|--------|  
|[\<binding\>](../../../../../docs/framework/misc/binding.md)|사용자 지정 바인딩의 모든 바인딩 기능을 정의합니다.|  
  
## 설명  
 `httpsTransport` 요소는 HTTPS 전송 프로토콜을 구현하는 사용자 지정 바인딩을 만들기 위한 시작점입니다.  HTTPS는 안전한 상호 운용성을 위해 사용되는 기본 전송입니다.  HTTPS는 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]에서 다른 웹 서비스 스택과의 상호 운용성을 보장하기 위해 지원됩니다.  
  
## 참고 항목  
 <xref:System.ServiceModel.Configuration.HttpsTransportElement>   
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>   
 <xref:System.ServiceModel.Channels.TransportBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [전송](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [전송 선택](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [바인딩](../../../../../docs/framework/wcf/bindings.md)   
 [바인딩 확장](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [사용자 지정 바인딩](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)