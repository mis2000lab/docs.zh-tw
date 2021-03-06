---
title: 如何：顯示 Windows Form ListView 控制項的圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 0e597ed182739947014b4f405ee2dc3149b62849
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>如何：顯示 Windows Form ListView 控制項的圖示
Windows Form<xref:System.Windows.Forms.ListView>控制項可以顯示三個影像清單中的圖示。 清單、 詳細資料，以及 SmallIcon 檢視會顯示從影像清單中指定的映像<xref:System.Windows.Forms.ListView.SmallImageList%2A>屬性。 使用 LargeIcon 檢視會顯示從影像清單中指定的映像<xref:System.Windows.Forms.ListView.LargeImageList%2A>屬性。 清單檢視也可以顯示一組額外的設定的圖示<xref:System.Windows.Forms.ListView.StateImageList%2A>大型或小型圖示旁邊的屬性。 如需影像清單的詳細資訊，請參閱[ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)和[如何： 加入或移除映像使用 Windows Form ImageList 元件](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  
  
### <a name="to-display-images-in-a-list-view"></a>在清單檢視中顯示影像  
  
1.  設定適當的屬性 —<xref:System.Windows.Forms.ListView.SmallImageList%2A>， <xref:System.Windows.Forms.ListView.LargeImageList%2A>，或<xref:System.Windows.Forms.ListView.StateImageList%2A>— 加入現有<xref:System.Windows.Forms.ImageList>您想要使用的元件。  
  
     使用 [屬性] 視窗中，在設計工具或程式碼，可以設定這些屬性。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  設定<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>或<xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A>屬性每個清單項目具有相關聯的圖示。  
  
     可以設定這些屬性，程式碼或內部**ListViewItem 集合編輯器**。 若要開啟**ListViewItem 集合編輯器**，按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.ListView.Items%2A>屬性**屬性**視窗。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>另請參閱  
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [操作說明：將資料行加入至 Windows Forms ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
