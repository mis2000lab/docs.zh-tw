---
title: 如何：取消 Parallel.For 或 ForEach 迴圈
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce9b8b0864f3ed30c2ff03866abdb0d5d07991db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>如何：取消 Parallel.For 或 ForEach 迴圈
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 方法可透過使用取消權杖來支援取消作業。 如需取消的詳細資訊，請參閱[取消](../../../docs/standard/threading/cancellation-in-managed-threads.md)。 在平行迴圈中，將 <xref:System.Threading.CancellationToken> 提供給 <xref:System.Threading.Tasks.ParallelOptions> 參數中的方法，然後將平行呼叫包含在 try catch 區塊中。  
  
## <a name="example"></a>範例  
 下列範例將示範如何取消呼叫 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>。 您可以套用相同的方法到 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 呼叫。  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 如果通知取消的權杖和 <xref:System.Threading.Tasks.ParallelOptions> 執行個體中指定的權杖相同，則平行迴圈在取消時將擲回單一 <xref:System.OperationCanceledException>。 如果是其他權杖導致取消，迴圈將會擲回<xref:System.AggregateException>，而其中的 <xref:System.OperationCanceledException> 是 InnerException。  
  
## <a name="see-also"></a>請參閱  
 [資料平行處理原則](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
