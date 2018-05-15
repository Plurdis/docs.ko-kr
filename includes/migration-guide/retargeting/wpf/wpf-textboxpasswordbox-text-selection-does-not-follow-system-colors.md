### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a><span data-ttu-id="53c88-101">WPF TextBox/PasswordBox 텍스트 선택은 시스템 색을 따르지 않음</span><span class="sxs-lookup"><span data-stu-id="53c88-101">WPF TextBox/PasswordBox Text Selection Does Not Follow System Colors</span></span>

|   |   |
|---|---|
|<span data-ttu-id="53c88-102">설명</span><span class="sxs-lookup"><span data-stu-id="53c88-102">Details</span></span>|<span data-ttu-id="53c88-103">.NET Framework 4.7.1 이전 버전에서 WPF <code>System.Windows.Controls.TextBox</code> 및 <code>System.Windows.Controls.PasswordBox</code>는 표시기(Adorner) 계층에서 텍스트 선택만 렌터링할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="53c88-103">In .NET Framework 4.7.1 and earlier versions, WPF <code>System.Windows.Controls.TextBox</code> and <code>System.Windows.Controls.PasswordBox</code> could only render a text selection in the Adorner layer.</span></span> <span data-ttu-id="53c88-104">일부 시스템 테마에서 텍스트를 가려서 읽기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53c88-104">In some system themes this would occlude text, making it hard to read.</span></span>  <span data-ttu-id="53c88-105">.NET Framework 4.7.2 이상 버전에서 개발자는 이 문제를 완화하는 비 표시기(Adorner) 기반 선택 렌더링 체계를 활성화하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53c88-105">In .NET Framework 4.7.2 and later, developers have an option of enabling a non-Adorner-based selection rendering scheme that alleviates this issue.</span></span>|
|<span data-ttu-id="53c88-106">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="53c88-106">Suggestion</span></span>|<span data-ttu-id="53c88-107">이 변경 내용을 활용하려는 개발자는 다음 AppContext 플래그를 적절하게 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53c88-107">A developer who wants to utilize this change must set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="53c88-108">이 기능을 사용하려면 설치된 .NET Framework 버전이 4.7.2 이상이어야 합니다. 비 표시기 기반 선택을 활성화하려면 다음 AppContext 플래그를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="53c88-108">To utilize this feature, the installed .NET Framework version must be 4.7.2 or greater.To enabled the non-adorner-based selection, use the following AppContext flag.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="53c88-109">범위</span><span class="sxs-lookup"><span data-stu-id="53c88-109">Scope</span></span>|<span data-ttu-id="53c88-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="53c88-110">Edge</span></span>|
|<span data-ttu-id="53c88-111">버전</span><span class="sxs-lookup"><span data-stu-id="53c88-111">Version</span></span>|<span data-ttu-id="53c88-112">4.7.2</span><span class="sxs-lookup"><span data-stu-id="53c88-112">4.7.2</span></span>|
|<span data-ttu-id="53c88-113">형식</span><span class="sxs-lookup"><span data-stu-id="53c88-113">Type</span></span>|<span data-ttu-id="53c88-114">대상 변경</span><span class="sxs-lookup"><span data-stu-id="53c88-114">Retargeting</span></span>|
