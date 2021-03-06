---
title: ICorDebugCode::GetILToNativeMapping 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13ec60999db88b9d7191a3866fcebe8098b4edee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping 方法
取得"COR_DEBUG_IL_TO_NATIVE_MAP 」 執行個體表示的對應從 Microsoft intermediate language (MSIL) 位移到原生位移的陣列。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cMap`  
 [in] `map` 陣列的大小。  
  
 `pcMap`  
 [out]項目中傳回的實際數目的指標`map`陣列。  
  
 `map`  
 [out]陣列`COR_DEBUG_IL_TO_NATIVE_MAP`結構，每個都表示從 MSIL 位移到原生位移的對應。  
  
 沒有任何排序傳回的元素的陣列。  
  
## <a name="remarks"></a>備註  
 `GetILToNativeMapping`才本例"ICorDebugCode"代表已在 just-in-time (JIT) 編譯的 MSIL 程式碼的原生程式碼，方法會傳回有意義的結果。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugCode 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
