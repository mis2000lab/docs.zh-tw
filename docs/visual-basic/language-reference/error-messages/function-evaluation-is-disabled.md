---
title: 函式評估已停用，因為先前的函式評估逾時
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 6231d48f3f90d8e436dc80bf4670886c1d030387
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>函式評估已停用，因為先前的函式評估逾時
函式評估已停用，因為先前的函式評估已經逾時。若要重新啟用函式評估，再次逐步執行或重新啟動偵錯。  
  
 在 Visual Studio 偵錯工具中，運算式指定程序呼叫，但另一個評估已逾時。  
  
 程序呼叫的逾時時間的可能原因包括無限迴圈或*無止盡迴圈*。 如需詳細資訊，請參閱[For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)。  
  
 無限迴圈的特殊案例是*遞迴*。 如需詳細資訊，請參閱[遞迴程序](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)。  
  
 **錯誤 ID:** BC30957  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  可能的話，請判斷先前的函式評估的已和原因逾時的時候。否則，您可能會遇到這個錯誤一次。  
  
2.  同樣地，逐步偵錯工具或終止，並重新啟動偵錯。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)  
 [使用偵錯工具巡覽程式碼](/visualstudio/debugger/navigating-through-code-with-the-debugger)
