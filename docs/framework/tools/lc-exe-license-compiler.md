---
title: Lc.exe(라이선스 컴파일러)
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: c5a8b38e819c323a06faad2edba586cb18d26edc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="lcexe-license-compiler"></a>Lc.exe(라이선스 컴파일러)
라이선스 컴파일러를 사용하면 라이선스 정보가 들어 있는 텍스트 파일을 읽고, 공용 언어 런타임 실행 파일에 리소스로 포함될 수 있는 바이너리 파일을 생성할 수 있습니다.  
  
 .licx 텍스트 파일은 폼에 라이센스가 있는 컨트롤을 추가할 때마다 Windows Forms 디자이너가 자동으로 생성하고 업데이트합니다. 컴파일의 일부로 프로젝트 시스템에서는 .licx 텍스트 파일을 .NET 컨트롤 라이선스를 지원하는 .licenses 이진 리소스로 변환합니다. 그러면 이진 리소스가 프로젝트 출력에 포함됩니다.  
  
 프로젝트를 빌드할 때 라이선스 컴파일러를 사용하면 32비트 및 64비트 간에 크로스 컴파일이 지원되지 않습니다. 그 이유는 라이선스 컴파일러가 어셈블리를 로드해야 하며 32비트 응용 프로그램에서 64비트 어셈블리를 로드하는 것은 허용되지 않으며 그 반대의 경우도 마찬가지입니다. 이 경우 명령줄의 라이선스 컴파일러를 사용하여 라이선스를 수동으로 컴파일하고 해당 아키텍처를 지정하세요.  
  
 이 도구는 자동으로 Visual Studio와 함께 설치됩니다. 이 도구를 실행하려면 개발자 명령 프롬프트(또는 Windows 7의 Visual Studio 명령 프롬프트)를 사용합니다. 자세한 내용은 [명령 프롬프트](../../../docs/framework/tools/developer-command-prompt-for-vs.md)를 참조하세요.  
  
 명령 프롬프트에 다음을 입력합니다.  
  
## <a name="syntax"></a>구문  
  
```  
      lc /target:  
      targetPE /complist:filename [/outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|옵션|설명|  
|------------|-----------------|  
|**/complist:** *filename*|.licenses 파일에 포함할 라이선스가 있는 구성 요소의 목록이 들어 있는 파일 이름을 지정합니다. 각 구성 요소는 한 줄에 하나의 구성 요소로 전체 이름을 사용하여 참조됩니다.<br /><br /> 명령줄 사용자는 프로젝트의 각 형식마다 별도의 파일을 지정할 수 있습니다. Lc.exe로 여러 개의 입력 파일을 사용하여 하나의 .licenses 파일을 생성할 수도 있습니다.|  
|**/h**[**elp**]|이 도구의 명령 구문 및 옵션을 표시합니다.|  
|**/i:** *모듈*|**/complist** 파일에 나열된 구성 요소가 들어 있는 모듈을 지정합니다. 모듈을 두 개 이상 지정하려면 여러 개의 **/i** 플래그를 사용합니다.|  
|**/nologo**|Microsoft 시작 배너를 표시하지 않습니다.|  
|**/outdir:** *path*|출력된 .licenses 파일을 포함할 디렉터리를 지정합니다.|  
|**/target:** *targetPE*|.licenses 파일이 생성되는 대상 실행 파일을 지정합니다.|  
|**/v**|세부 정보 표시 모드를 지정합니다. 즉, 컴파일 진행 정보를 표시합니다.|  
|**@** *파일*|지시 파일(.rsp)을 지정합니다.|  
|**/?**|이 도구의 명령 구문 및 옵션을 표시합니다.|  
  
## <a name="example"></a>예  
  
1.  `HostApp.exe`라는 응용 프로그램의 `Samples.DLL`에 들어 있는 라이선스가 있는 컨트롤 `MyCompany.Samples.LicControl1`을 사용하는 경우 다음 내용이 들어 있는 `HostAppLic.txt`를 만들 수 있습니다.  
  
    ```  
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2.  다음 명령을 사용하여 `HostApp.exe.licenses`라는 .licenses 파일을 만듭니다.  
  
    ```  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3.  해당 .licenses 파일을 리소스로 포함하는 `HostApp.exe`를 빌드합니다. C# 응용 프로그램을 빌드하는 경우에는 다음 명령을 사용하여 해당 응용 프로그램을 빌드합니다.  
  
    ```  
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 다음 명령을 사용하여 `myApp.licenses`, `hostapplic.txt` 및 `hostapplic2.txt`로 지정된, 라이선스가 있는 구성 요소 목록에서 `hostapplic3.txt`를 컴파일하고, `modulesList` 인수를 사용하여 라이선스가 있는 구성 요소가 들어 있는 모듈을 지정합니다.  
  
```  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a>지시 파일 예  
 다음 목록에서는 지시 파일의 예로 `response.rsp`를 보여 줍니다. 지시 파일에 대한 자세한 내용은 [지시 파일](/visualstudio/msbuild/msbuild-response-files)을 참조하세요.  
  
```  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
```  
  
 다음 명령줄은 `response.rsp` 파일을 사용합니다.  
  
```  
lc @response.rsp  
```  
  
## <a name="see-also"></a>참고 항목  
 [도구](../../../docs/framework/tools/index.md)  
 [Al.exe(어셈블리 링커)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [명령 프롬프트](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
