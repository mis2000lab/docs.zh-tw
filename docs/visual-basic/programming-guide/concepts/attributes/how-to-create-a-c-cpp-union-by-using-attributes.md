---
title: 如何： 使用屬性 (Visual Basic) 建立的 C + + 等位
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: b07168df3fb7ec8195a3f64ef5b1bef0cc16dda2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>如何： 使用屬性 (Visual Basic) 建立的 C/c + + 等位
您可以使用屬性，自訂如何在記憶體中配置結構。 例如，您可以使用 `StructLayout(LayoutKind.Explicit)` 和 `FieldOffset` 屬性，以 C/C++ 建立所謂的等位。  
  
## <a name="example"></a>範例  
 在此程式碼片段中，`TestUnion` 的所有欄位都在記憶體的同一位置開始。  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
<System.Runtime.InteropServices.StructLayout(   
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestUnion  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public i As Integer  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public d As Double  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public c As Char  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public b As Byte  
End Structure  
```  
  
## <a name="example"></a>範例  
 以下是另一個範例，欄位從明確設定的不同位置開始。  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
 <System.Runtime.InteropServices.StructLayout(  
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestExplicit  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public lg As Long  
  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public i1 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(4)>   
     Public i2 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(8)>   
     Public d As Double  
  
     <System.Runtime.InteropServices.FieldOffset(12)>   
     Public c As Char  
  
     <System.Runtime.InteropServices.FieldOffset(14)>   
     Public b As Byte  
 End Structure  
```  
  
 `i1` 和 `i2` 這兩個整數欄位和 `lg` 共用相同的記憶體位置。 使用平台叫用時，這種結構配置控制項很有用。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Visual Basic 程式設計手冊](../../../../visual-basic/programming-guide/index.md)  
 [屬性](../../../../standard/attributes/index.md)  
 [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [屬性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [建立自訂屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [使用反映存取屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
