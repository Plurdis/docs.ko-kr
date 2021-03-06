---
title: ICorDebugModule2::ResolveAssembly 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a6596807b98e6c8b8624b5df18f78dbf8d0711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule2resolveassembly-method"></a>ICorDebugModule2::ResolveAssembly 메서드
지정한 메타 데이터 토큰에서 참조 하는 어셈블리를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT ResolveAssembly (  
    [in]  mdToken             tkAssemblyRef,  
    [out] ICorDebugAssembly   **ppAssembly  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `tkAsemblyRef`  
 [in] `mdToken` 어셈블리를 참조 하는 값입니다.  
  
 `ppAssembly`  
 [out] 어셈블리를 나타내는 ICorDebugAssembly 개체의 주소에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  
 어셈블리가 아직 로드 되지 않은 경우 경우 `ResolveAssembly` 호출 되는 HRESULT CORDBG_E_CANNOT_RESOLVE_ASSEMBLY의 값이 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET framework 버전:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
