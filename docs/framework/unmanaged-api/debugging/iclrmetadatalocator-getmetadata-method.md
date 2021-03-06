---
title: ICLRMetadataLocator::GetMetadata 方法
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4338619414c9c9ac8c5fe85479562410d1678698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata 方法
呼叫由 common language runtime (CLR) 資料存取服務擷取映像的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `imagePath`  
 [in]字串，指定影像檔的路徑。  
  
 `imageTimestamp`  
 [in]映像檔的時間戳記。  
  
 `imageSize`  
 [in]映像檔的大小。  
  
 `mvid`  
 [in]影像的全域唯一識別項。  
  
 `mdRva`  
 [in]相對虛擬位址 (RVA) 的中繼資料。 位址是相對於映像的基底位址。  
  
 `flags`  
 [in]保留供未來使用。  
  
 `bufferSize`  
 [in]要放置中繼資料的緩衝區大小。  
  
 `buffer`  
 [out]要放置中繼資料緩衝區。  
  
 `dataSize`  
 [out]傳回中繼資料的大小。  
  
## <a name="remarks"></a>備註  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl、 ClrData.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRMetadataLocator 介面](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
