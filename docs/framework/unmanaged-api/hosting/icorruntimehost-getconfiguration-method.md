---
title: ICorRuntimeHost::GetConfiguration 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c51ddae6aa62552bac9990b57a173c28f73bae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehostgetconfiguration-method"></a>ICorRuntimeHost::GetConfiguration 方法
取得物件，可讓主機指定的 common language runtime (CLR) 回呼組態。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pConfiguration`  
 [out]位址指標[ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)可以用來設定 CLR 物件。  
  
## <a name="remarks"></a>備註  
 初始化; 之前，必須設定 CLR否則，`GetConfiguration`方法會傳回 HRESULT，指出錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** 1.0、 1.1  
  
## <a name="see-also"></a>另請參閱  
 [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
