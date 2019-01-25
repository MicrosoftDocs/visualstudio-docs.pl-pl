---
title: Boundsrules — ograniczenie lokalizacji i rozmiaru kształtu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d09be82be084767bfb2d300a1877e95456a957b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779272"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules — ograniczenie lokalizacji i rozmiaru kształtu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A *reguły granice* jest klasa, która definiuje ograniczenia na rozmiar i położenie kształtu. Zapewnia metodę, która często jest wywoływana, gdy użytkownik przeciąga kształtu lub rogów lub stron kształtu.  
  
 Poniższy przykład ogranicza prostokątnego kształtu do paska o stałym rozmiarze, poziomej lub pionowej. Gdy użytkownik przeciągnie rogów lub stron, konspektu Przerzuca między dwie konfiguracje dozwolonych wysokość i szerokość.  
  
 Granice reguły jest klasa jest pochodną <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. W kształcie, tworzone jest wystąpienie reguły:  
  
```  
using Microsoft.VisualStudio.Modeling.Diagrams; ...  
public partial class BarShape  
{  
  /// <summary>  
  /// Rule invoked when the user is resizing a shape.  
  /// </summary>  
  public override BoundsRules BoundsRules  
  { get { return new BarBoundsRule(); } }  
}  
/// <summary>  
/// Rule invoked when the user is changing a shape's outline.  
/// Provides real-time mouse rubber-band feedback, so must work fast.  
/// </summary>  
public class BarBoundsRule: BoundsRules  
{   
  public override RectangleD GetCompliantBounds   
     (ShapeElement shape, RectangleD proposedBounds)  
  {  
    double thickness = 0.1;  
    if (proposedBounds.Height > proposedBounds.Width)  
    {  
      // There is a minimum width for a shape; the width  
      // will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
            new SizeD(thickness, proposedBounds.Height));  
    }  
    else  
    {  
      // There is a minimum height for a shape; the   
      // height will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
         new SizeD(proposedBounds.Width, thickness));  
} } }  
```  
  
 Należy zauważyć, że lokalizacja i rozmiar może być ograniczona, jeśli chcesz.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Odpowiadanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)
