---
title: 範圍變數&lt;變數&gt;隱藏了封閉區塊、 預先定義的範圍變數或查詢運算式中隱含宣告的變數中的變數
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: f02533cf7cb79c34e5bb5a6d445aaef7ab0e86da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>範圍變數&lt;變數&gt;隱藏了封閉區塊、 預先定義的範圍變數或查詢運算式中隱含宣告的變數中的變數
中指定的範圍變數名稱`Select`， `From`， `Aggregate`，或`Let`子句會重複已經在查詢或查詢所隱含宣告的變數名稱中先前指定的範圍變數的名稱例如，欄位名稱或彙總函式的名稱。  
  
 **錯誤 ID:** BC36633  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定特定查詢範圍中的所有範圍變數都有唯一的名稱。 您可以將查詢括在括號可確保巢狀的查詢具有唯一的範圍中。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Let 子句](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
