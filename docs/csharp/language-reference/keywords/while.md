---
title: while (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 23c5ca3bb7dc401a894a6c3918fbaec9a9306153
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="while-c-reference"></a>while (C# 參考)
`while` 陳述式會執行陳述式或陳述式區塊，直到指定的運算式評估為 `false` 為止。  
  
## <a name="example"></a>範例  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a>範例  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a>範例  
 `while` 運算式的測試是在每次執行迴圈之前發生，因此 `while` 迴圈會執行零次或多次。 這與 [do](../../../csharp/language-reference/keywords/do.md) 迴圈不同，此迴圈會執行一次或多次。  
  
 [break](../../../csharp/language-reference/keywords/break.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式將控制權轉移到迴圈外部時，即可終止 `while` 迴圈。 若要將控制權傳遞給下一個反覆運算，而不結束迴圈，請使用 [continue](../../../csharp/language-reference/keywords/continue.md) 陳述式。 請注意三個先前範例中的輸出差異，根據遞增 `int n` 的位置而定。 在下面的範例中，不會產生任何輸出。  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [while 陳述式 (C++)](/cpp/cpp/while-statement-cpp)  
 [反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md)
