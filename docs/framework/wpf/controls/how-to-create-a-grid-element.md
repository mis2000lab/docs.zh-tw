---
title: 如何：建立 Grid 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: 9fc70b8f15c4ecb4844c9c2ff4f7eeab94e7b906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-grid-element"></a>如何：建立 Grid 項目
## <a name="example"></a>範例  
 下列範例示範如何建立和使用的執行個體<xref:System.Windows.Controls.Grid>使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]或程式碼。 這個範例會使用三個<xref:System.Windows.Controls.ColumnDefinition>物件和三個<xref:System.Windows.Controls.RowDefinition>物件建立一個方格，其中擁有九個資料格，例如工作表。 每個資料格包含<xref:System.Windows.Controls.TextBlock>項目，表示資料及上方資料列包含<xref:System.Windows.Controls.TextBlock>與<xref:System.Windows.Controls.Grid.ColumnSpan%2A>套用的屬性。 若要顯示的界限，每個資料格，<xref:System.Windows.Controls.Grid.ShowGridLines%2A>屬性已啟用。  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Grid>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)
