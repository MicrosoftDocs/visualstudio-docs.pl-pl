---
title: Kontrolowanie koloru, stylu linii i innych właściwości kształtu
description: Zawiera informacje na temat kontrolowania właściwości kształtu, takich jak styl koloru i linii.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 836c77f3651b7686e9366fe75ea7922a248fd28f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389634"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Kontrolowanie koloru, stylu linii i innych właściwości kształtu

Niektóre właściwości kształtu, takie jak kolor, mogą być "widoczne". Oznacza to, że właściwości można połączyć z właściwością domeny kształtu. Inne muszą być kontrolowane bezpośrednio.

## <a name="exposing-a-property"></a>Udostępnianie właściwości
 Niektóre właściwości kształtu, takie jak kolor, można połączyć z wartością właściwości domeny.

 W definicji DSL wybierz kształt, łącznik lub klasę diagramu. W menu po kliknięciu prawym przyciskiem myszy wybierz pozycję **Dodaj ujawnione,** a następnie wybierz odpowiednią właściwość, na przykład Kolor wypełnienia.

 Kształt ma teraz właściwość domeny, która można ustawić w kodzie programu lub jako użytkownik.

## <a name="dynamically-updating-an-exposed-property"></a>Dynamiczne aktualizowanie widocznej właściwości
 Zazwyczaj chcesz, aby ujawniona właściwość zależała od innej właściwości. Na przykład możesz chcieć, aby kształt był czerwony za każdym razem, gdy właściwość określonej domeny jest mniejsza od zera. Aby utworzyć tę zależność, utwórz [regułę](../modeling/rules-propagate-changes-within-the-model.md). Na przykład:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```