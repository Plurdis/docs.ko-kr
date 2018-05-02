### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="1e329-101">MinFreeMemoryPercentageToActiveService가 지금 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e329-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1e329-102">설명</span><span class="sxs-lookup"><span data-stu-id="1e329-102">Details</span></span>|<span data-ttu-id="1e329-103">이 설정은 WCF 서비스 활성화를 위해 서버에서 사용할 수 있는 최소 메모리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e329-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="1e329-104">또한 이 설정은 <xref:System.OutOfMemoryException?displayProperty=name> 예외가 발생되지 않도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1e329-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=name> exceptions.</span></span> <span data-ttu-id="1e329-105">.NET Framework 4.5에서 이 설정은 영향을 주지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="1e329-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="1e329-106">.NET Framework 4.5.1에서 해당 설정이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e329-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>|
|<span data-ttu-id="1e329-107">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="1e329-107">Suggestion</span></span>|<span data-ttu-id="1e329-108">웹 서버의 사용 가능한 메모리가 구성 설정에서 정의된 백분율보다 적은 경우 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1e329-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="1e329-109">성공적으로 시작되었지만 제한된 메모리 환경에서 실행되는 일부 WCF 서비스의 경우 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e329-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>|
|<span data-ttu-id="1e329-110">범위</span><span class="sxs-lookup"><span data-stu-id="1e329-110">Scope</span></span>|<span data-ttu-id="1e329-111">부</span><span class="sxs-lookup"><span data-stu-id="1e329-111">Minor</span></span>|
|<span data-ttu-id="1e329-112">버전</span><span class="sxs-lookup"><span data-stu-id="1e329-112">Version</span></span>|<span data-ttu-id="1e329-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="1e329-113">4.5.1</span></span>|
|<span data-ttu-id="1e329-114">형식</span><span class="sxs-lookup"><span data-stu-id="1e329-114">Type</span></span>|<span data-ttu-id="1e329-115">런타임</span><span class="sxs-lookup"><span data-stu-id="1e329-115">Runtime</span></span>|
