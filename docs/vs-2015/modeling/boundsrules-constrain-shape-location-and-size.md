---
title: BoundsRules — ograniczenia lokalizacji i rozmiaru kształtu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d660189ede0848216eb44d6ef49fe9c93a06ec8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672729"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules — ograniczenie lokalizacji i rozmiaru kształtu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Reguła granic* jest klasą, która definiuje limity rozmiaru i lokalizacji kształtu. Zapewnia metodę, która jest wywoływana wielokrotnie, gdy użytkownik przeciąga kształt lub narożniki lub boki kształtu.

 Poniższy przykład ogranicza kształt prostokątny jako pasek o stałym rozmiarze, poziomo lub pionowo. Gdy użytkownik przeciągnie rogów lub boki, kontur przewraca między dwoma dozwolonymi konfiguracjami wysokości i szerokości.

 Reguła granic jest klasą pochodną <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Wystąpienie reguły jest tworzone w kształcie:

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

 Należy zauważyć, że w razie potrzeby można ograniczyć lokalizację i rozmiar.

## <a name="see-also"></a>Zobacz też
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> [Odpowiadanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)
