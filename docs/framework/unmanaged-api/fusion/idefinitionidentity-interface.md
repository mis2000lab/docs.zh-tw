---
title: IDefinitionIdentity 介面
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 401c23e44cc473d0a27a82a00343852693cb0f2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity 介面
代表目前範圍中定義的應用程式的程式碼的唯一的簽章。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|取得新的介面指標`IDefinitionIdentity`物件與此相同`IDefinitionIdentity`，除非有指定的屬性變更。|  
|`IDefinitionIdentity::EnumAttributes`|取得的介面指標[IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)物件，其中包含與此相關聯的屬性`IDefinitionIdentity`。|  
|`IDefinitionIdentity::GetAttribute`|指定的命名空間中取得具有指定名稱之屬性的值。|  
|`IDefinitionIdentity::SetAttribute`|設定為指定的值指定的命名空間中具有指定的名稱的屬性。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
