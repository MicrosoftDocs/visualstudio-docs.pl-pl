---
title: BoundsRules — ograniczenie lokalizacji i rozmiaru kształtu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 449fb0c12b11163ba0ceca981e66a7da0c399e1c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950202"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules — ograniczenie lokalizacji i rozmiaru kształtu

A *reguły granice* jest klasa, która definiuje ograniczenia na rozmiar i położenie kształtu. Zapewnia metodę, która często jest wywoływana, gdy użytkownik przeciąga kształtu lub rogów lub stron kształtu.

Poniższy przykład ogranicza prostokątnego kształtu do paska o stałym rozmiarze, poziomej lub pionowej. Gdy użytkownik przeciągnie rogów lub stron, konspektu Przerzuca między dwie konfiguracje dozwolonych wysokość i szerokość.

Granice reguły jest klasa jest pochodną <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. W kształcie, tworzone jest wystąpienie reguły:

```csharp
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

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
- [Odpowiadanie na zmiany i ich propagowanie](../modeling/responding-to-and-propagating-changes.md)