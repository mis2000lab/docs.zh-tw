---
title: 如何：停用加入和刪除 DataRepeater 項目 (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: e3d0d2a8d422054e269ee92df1fdfcb5acb96eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a>如何：停用加入和刪除 DataRepeater 項目 (Visual Studio)
根據預設，使用者可以新增或刪除的項目<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 使用者可以按 CTRL + N 加入新項目時<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>焦點或按一下**AddNewItem**按鈕<xref:System.Windows.Forms.BindingNavigator>控制項。 使用者可以藉由按下刪除的項目刪除時<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>焦點或按一下**DeleteItem**按鈕<xref:System.Windows.Forms.BindingNavigator>控制項。  
  
 新增及/或刪除在設計階段或執行階段，您可以停用。  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a>若要停用加入和刪除在設計階段  
  
1.  在 Windows Form 設計工具中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
    > [!NOTE]
    >  您必須選取控制項的較低的區段。 如果您選取項目範本 > 一節，將會顯示一組不同的屬性。  
  
2.  在 [屬性] 視窗中，設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A>屬性**False**。  
  
3.  設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A>屬性**False**。  
  
4.  在 Windows Form 設計工具中，選取 <xref:System.Windows.Forms.BindingNavigator>控制項，然後再按一下**AddNewItem**按鈕 （在其上的加號按鈕）。  
  
5.  在 [屬性] 視窗中，設定<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>屬性**False**。  
  
6.  在 Windows Form 設計工具中，選取 <xref:System.Windows.Forms.BindingNavigator>控制項，然後再按一下**DeleteItem**按鈕 （具有紅色 X 上的按鈕）。  
  
7.  在 [屬性] 視窗中，設定<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>屬性**False**。  
  
8.  在元件匣中，選取<xref:System.Windows.Forms.BindingSource>的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>繫結。  
  
9. 在 [屬性] 視窗中，設定<xref:System.Windows.Forms.BindingSource.AllowNew%2A>屬性**False**。  
  
10. 在 [Windows Form 設計工具中，按兩下**DeleteItem** ] 按鈕以開啟程式碼編輯器。  
  
11. 在 [事件] 下拉式清單中，選取`BindingNavigatorDeleteItem_EnabledChanged`事件。  
  
12. 將下列程式碼加入至 `BindingNavigatorDeleteItem_EnabledChanged` 事件處理常式：  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  這是必要步驟，因為每次目前資料錄變更時， <xref:System.Windows.Forms.BindingSource> 都會啟用 [DeleteItem]  按鈕。  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a>若要停用加入和刪除執行階段  
  
1.  在 [Windows Form 設計工具] 中，按兩下表單開啟 [程式碼編輯器]。  
  
2.  將下列程式碼加入 `Form_Load` 事件：  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  將下列程式碼加入至 `BindingNavigatorDeleteItem_EnabledChanged` 事件處理常式：  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  這是必要步驟，因為每次目前資料錄變更時， <xref:System.Windows.Forms.BindingSource> 都會啟用 [DeleteItem]  按鈕。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
