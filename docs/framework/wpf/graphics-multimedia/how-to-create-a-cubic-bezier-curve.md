---
title: '방법: 입방형 3차원 곡선 만들기'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 6332129179e1934e5a37c7a1a40ef5f46ab669a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>방법: 입방형 3차원 곡선 만들기
이 예제에는 입방 형 3 차원 곡선을 만드는 방법을 보여 줍니다. 입방 형 3 차원 곡선을을 만들려면 사용는 <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, 및 <xref:System.Windows.Media.BezierSegment> 클래스입니다.  기를 표시 하려면 사용을 <xref:System.Windows.Shapes.Path> 요소를 함께 사용 하거나 한 <xref:System.Windows.Media.GeometryDrawing> 또는 <xref:System.Windows.Media.DrawingContext>합니다. 다음 예에서 입방 형 3 차원 곡선에서 그려집니다 (10, 100)에 (300, 100). 곡선의 제어점에 (100, 0) 및 (200, 200).  
  
## <a name="example"></a>예제  
 [xaml]  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], 약식된 태그 구문을 사용 하 여 경로 나타낼 수 있습니다.  
  
 [!code-xaml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 [xaml]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], 개체 태그를 사용 하 여 입방 형 3 차원 곡선을 그릴 수도 있습니다. 다음 예제는 이전 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 예제와 동일합니다.  
  
 [!code-xaml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 이 예제는 더 큰 샘플에 속합니다. 전체 샘플을 보려면 [기하 도형 샘플](http://go.microsoft.com/fwlink/?LinkID=159989)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [타원형 원호 만들기](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [PathGeometry에 LineSegment 만들기](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)  
 [입방형 3차원 곡선 만들기](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)  
 [정방형 3차원 곡선 만들기](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)
