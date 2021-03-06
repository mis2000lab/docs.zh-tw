---
title: CompareTo 函式 （Unmanaged API 參考）
description: CompareTo 函式會比較的另一個 WMI 物件的物件。
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db4431da90842f4f96a0f09a2f28dc473d956ee3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compareto-function"></a>CompareTo 函式
比較物件與另一個 Windows 管理物件。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`flags`  
[in]指定要比較的物件特性的旗標的位元組合。 請參閱[備註](#remarks)節的詳細資訊。

`pCompareTo`  

[in]比較的物件。 `pcompareTo` 必須是有效[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體; 它不能`null`。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 發生意外的錯誤。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | 第二個呼叫`BeginEnumeration`所沒有的中間呼叫[ `EndEnumeration` ](endenumeration.md)。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_DIFFERENT` | 0x40003 | 物件有不同。 |
| `WBEM_S_SAME` | 0 | 物件是相同的比較旗標為基礎。 |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx)方法。

可以做為傳遞的旗標`lEnumFlags`引數中所定義*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中。 您可以藉由指定下列旗標的位元組合，指定比較中涉及的個別特性：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | 忽略來源 （伺服器和來源的命名空間）。 |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | 略過所有限定詞 (包括**金鑰**和**動態**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | 略過屬性的預設值。 這個旗標僅適用於比較的類別。 |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | 忽略限定詞標註。 這個旗標仍限定詞納入考量，但會忽略類型差異，例如傳播規則並覆寫限制。 |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | 忽略大小寫比較字串值。 這適用於字串和辨識符號值。 比較的屬性和限定詞的名稱永遠是區分大小寫，不論設定這個旗標。 |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | 假設要比較之物件都屬於相同的類別序列。 因此，此旗標會比較只執行個體的相關資訊。 您可以使用這個旗標來最佳化效能。 如果物件不是類別的相同，則結果會是類別的未定義。 |

或者，您可以指定單一複合旗標，如下所示：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | 請考慮在比較中的所有功能。 |

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
