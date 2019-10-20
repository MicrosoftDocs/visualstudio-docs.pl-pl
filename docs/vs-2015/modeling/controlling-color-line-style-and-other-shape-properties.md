---
title: Kontrolowanie koloru, stylu linii i innych właściwości kształtu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5d296f5ab3f5c584558b373b57c175fb2bacef4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667857"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Kontrolowanie koloru, stylu linii i innych właściwości kształtu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niektóre właściwości kształtu, takie jak kolor mogą być "uwidocznione" — czyli połączone z właściwością domeny kształtu. Inne osoby muszą być kontrolowane bezpośrednio.

## <a name="exposing-a-property"></a>Uwidacznianie właściwości
 Niektóre właściwości kształtu, takie jak kolor, można połączyć z wartością właściwości domeny.

 W definicji DSL wybierz kształt, łącznik lub klasę diagramu. W menu kontekstowym wybierz polecenie **Dodaj uwidocznione**, a następnie wybierz żądaną właściwość, taką jak kolor wypełnienia.

 Kształt ma teraz właściwość domeny, którą można ustawić w kodzie programu lub jako użytkownik.

## <a name="dynamically-updating-an-exposed-property"></a>Dynamiczne aktualizowanie uwidocznionej właściwości
 Zazwyczaj chcesz uczynić uwidocznioną Właściwość zależną od innej właściwości. Na przykład możesz chcieć, aby kształt wyłączał kolor czerwony, gdy określona właściwość domeny jest mniejsza od zera. Aby utworzyć Tę zależność, Utwórz [regułę](../modeling/rules-propagate-changes-within-the-model.md). Na przykład:

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
