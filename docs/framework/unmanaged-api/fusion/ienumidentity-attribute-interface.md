---
title: IEnumIDENTITY_ATTRIBUTE 介面
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da6462a320b1f090940473f566ade91d36e74780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ienumidentityattribute-interface"></a>IEnumIDENTITY_ATTRIBUTE 介面
可做為目前範圍中的程式碼物件的屬性的列舉值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|取得新的介面指標`IEnumIDENTITY_ATTRIBUTE`，其中包含這個相同的成員`IEnumIDENTITY_ATTRIBUTE`。|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|將這個項目中所包含的資料寫入`IEnumIDENTITY_ATTRIBUTE`指定的資料緩衝區。|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|取得指定的數目的屬性，從目前位置開始。|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|將指令指標移到開頭`IEnumIDENTITY_ATTRIBUTE`。|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|將指令指標向前移以指定的項目，從目前位置開始。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
