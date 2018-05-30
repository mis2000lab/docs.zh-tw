---
title: LINQ to Entities 中的查詢
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 27e547dacb41201f00552c58840c70ca8fa34428
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="queries-in-linq-to-entities"></a>LINQ to Entities 中的查詢
查詢是指從資料來源中擷取資料的運算式。 查詢通常會以特定的查詢語言來表示，例如 SQL 用於關聯式資料庫，而 XQuery 用於 XML。 因此，開發人員必須針對他們所查詢的每種資料來源或資料格式，學習新的查詢語言。 Language-Integrated Query (LINQ) 提供了一種較簡單且一致的模型，可處理各種資料來源和格式的資料。 在 LINQ 查詢中，您一定會使用程式設計物件。  
  
 LINQ 查詢作業由三個動作構成：取得資料來源、建立查詢和執行查詢。  
  
 實作 <xref:System.Collections.Generic.IEnumerable%601> 泛型介面或 <xref:System.Linq.IQueryable%601> 泛型介面的資料來源可以透過 LINQ 進行查詢。 泛型執行個體<xref:System.Data.Objects.ObjectQuery%601>類別，實作泛型<xref:System.Linq.IQueryable%601>介面中，做為資料來源[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]查詢。 <xref:System.Data.Objects.ObjectQuery%601> 泛型類別表示傳回零個或多個具型別物件之集合的查詢。 您也可以讓編譯器推斷實體類型，使用 C# 關鍵字`var`（在 Visual Basic 中寫成 Dim）。  
  
 在此查詢中，您可以精確地指定想要從資料來源中擷取的資訊。 此外，查詢也可以指定該項資訊傳回之前應該如何排序、分組和成形。 在 LINQ 中，查詢會儲存在變數內。 如果查詢傳回一連串值，查詢變數本身必須是可查詢型別。 這個查詢變數不會採取任何動作，也不會傳回任何資料。它只會儲存查詢資訊。 在您建立查詢之後，必須執行該查詢以便擷取任何資料。  
  
## <a name="query-syntax"></a>查詢語法  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢可以使用兩個不同的語法來撰寫： 查詢運算式語法和以方法為基礎的查詢語法。 查詢運算式語法是 C# 3.0 和 Visual Basic 9.0 中的新功能，它是一組以類似 TRANSACT-SQL 或 XQuery 的宣告式語法撰寫的子句組成。 不過，[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] Common Language Runtime (CLR) 無法讀取查詢運算式語法本身。 因此，在編譯期間，查詢運算式會轉譯為 CLR 可以了解的項目：即方法呼叫。 這些方法稱為*標準查詢運算子*。 身為開發人員，您可以選擇使用方法語法來直接呼叫它們，而非使用查詢語法。 如需詳細資訊，請參閱 [LINQ 中的查詢語法及方法語法](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。  
  
### <a name="query-expression-syntax"></a>查詢運算式語法  
 查詢運算式是宣告式查詢語法。 這些語法可以讓開發人員以類似 Transact-SQL 格式的高階語言撰寫查詢。 透過使用查詢運算式語法，您就可以利用最少的程式碼，針對資料來源執行同樣複雜的篩選、排序和分組作業。 如需詳細資訊，[基本查詢作業 (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md)。 如需示範如何使用查詢運算式語法的範例，請參閱下列主題：  
  
-   [查詢運算式語法範例：投影](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
-   [查詢運算式語法範例：篩選](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
-   [查詢運算式語法範例：排序](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
-   [查詢運算式語法範例：彙總運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [查詢運算式語法範例：資料分割](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
-   [查詢運算式語法範例：聯結運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
-   [查詢運算式語法範例：項目運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
-   [查詢運算式語法範例：群組](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
-   [查詢運算式語法範例：導覽關聯性](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>以方法為基礎的查詢語法  
 另一種撰寫 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢的方式是使用以方法為基礎的查詢。 以方法為基礎的查詢語法是對 LINQ 運算子方法，並傳遞 lambda 運算式當做參數的直接方法呼叫的序列。 如需詳細資訊，請參閱 [Lambda 運算式](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。 如需示範如何使用以方法為基礎的語法之範例，請參閱下列主題：  
  
-   [以方法為基礎的查詢語法範例：投影](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
-   [以方法為基礎的查詢語法範例：篩選](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
-   [以方法為基礎的查詢語法範例：排序](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
-   [以方法為基礎的查詢語法範例：彙總運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [以方法為基礎的查詢語法範例：資料分割](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
-   [以方法為基礎的查詢語法範例：轉換](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
-   [以方法為基礎的查詢語法範例：聯結運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
-   [以方法為基礎的查詢語法範例：項目運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
-   [以方法為基礎的查詢語法範例：群組](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
-   [以方法為基礎的查詢語法範例：導覽關聯性](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [開始使用 C# 中的 LINQ](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [使用 Visual Basic 撰寫 LINQ 入門](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Entity Framework 合併選項和已編譯的查詢](http://go.microsoft.com/fwlink/?LinkId=199591)
