---
title: 如何：使用 Polygon 項目繪製封閉的形狀
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 4105139e159783cf0197f4e56c82001835077cbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>如何：使用 Polygon 項目繪製封閉的形狀
這個範例示範如何使用來繪製封閉的圖形<xref:System.Windows.Shapes.Polygon>項目。 若要繪製封閉的圖形，請建立<xref:System.Windows.Shapes.Polygon>項目，並使用其<xref:System.Windows.Shapes.Polygon.Points%2A>屬性可指定圖形的頂點。 繪製線條，會自動連接的第一個和最後一個點。 最後，指定<xref:System.Windows.Shapes.Shape.Fill%2A>、 <xref:System.Windows.Shapes.Shape.Stroke%2A>，或兩者。  
  
## <a name="example"></a>範例  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，點的有效語法是以空格分隔清單的逗號分隔 x 和 y 座標組。  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 雖然此範例會使用<xref:System.Windows.Controls.Canvas>包含多邊形，使用多邊形元素 （和其他所有圖形項目） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。  
  
 這個範例是較大範例的一部分如需完整範例，請參閱[圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)。
