---
title: Aktualizowanie kształtów i łączników, aby odzwierciedlały model
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a43e8570ea65373b8cac0bd3e3e7a8dc1f5791
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115027"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Aktualizowanie kształtów i łączników, aby odzwierciedlały model

W języku specyficznym dla domeny w programie Visual Studio, można sprawić, aby wygląd kształtu odzwierciedlał stan modelu bazowego.

Przykłady kodu w tym temacie należy dodać do pliku `.cs` w `Dsl` projekcie. W każdym pliku są wymagane następujące dyrektywy:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Ustaw właściwości mapy kształtów, aby kontrolować widoczność elementu Dekoratora

Można kontrolować widoczność dekoratora bez pisania kodu programu, konfigurując mapowanie między kształtem i klasą domeny w definicji DSL. Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Uwidocznienie koloru i stylu kształtu jako właściwości

W definicji DSL kliknij prawym przyciskiem myszy klasę Shape, wskaż polecenie **Dodaj uwidocznione**, a następnie kliknij jeden z elementów, takich jak **kolor wypełnienia**.

Kształt ma teraz właściwość domeny, którą można ustawić w kodzie programu lub jako użytkownik. Na przykład, aby ustawić go w kodzie programu dla polecenia lub reguły, można napisać:

`shape.FillColor = System.Drawing.Color.Red;`

Jeśli chcesz uczynić zmienną właściwości tylko pod kontrolą programu, a nie przez użytkownika, wybierz nową właściwość domeny, taką jak **kolor wypełnienia** na DIAGRAMIE definicji DSL. Następnie w okno Właściwości ustawić wartość **umożliwia przeglądania** na `false` lub Set **jest interfejsem użytkownika ReadOnly** do `true`.

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definiowanie reguł zmiany w celu uzyskania koloru, stylu lub lokalizacji zależy od właściwości elementu modelu
 Można zdefiniować reguły, które aktualizują wygląd kształtu zależnego od innych części modelu. Na przykład można zdefiniować regułę zmiany dla elementu modelu, który aktualizuje kolor kształtu zależnie od właściwości elementu modelu. Aby uzyskać więcej informacji na temat reguł zmiany, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

 Reguł należy używać tylko do aktualizowania właściwości, które są przechowywane w magazynie, ponieważ reguły nie są wywoływane po wykonaniu polecenia Cofnij. Nie obejmuje to niektórych funkcji graficznych, takich jak rozmiar i widoczność kształtu. Aby zaktualizować te funkcje kształtu, zobacz [aktualizowanie funkcji graficznych](#OnAssociatedProperty)nienależących do magazynu.

 W poniższym przykładzie założono, że masz uwidocznioną `FillColor` jako właściwość domeny, zgodnie z opisem w poprzedniej sekcji.

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }
```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Użyj OnChildConfigured, aby zainicjować właściwości kształtu

Aby ustawić właściwości kształtu podczas jego pierwszego tworzenia, przesłonięcie `OnChildConfigured()` w częściowej definicji klasy diagramu. Klasa diagram jest określona w definicji DSL, a wygenerowany kod znajduje się w **Dsl\Generated Code\Diagram.cs**. Na przykład:

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}
```

Tej metody można używać zarówno w przypadku właściwości domeny, jak i funkcji niezwiązanych z magazynem, takich jak rozmiar kształtu.

## <a name="OnAssociatedProperty"></a>Używanie AssociateValueWith () do aktualizowania innych funkcji kształtu

W przypadku niektórych funkcji kształtu, takich jak to, czy ma on cień, czy styl strzałki łącznika, nie ma wbudowanej metody ujawniania funkcji jako właściwości domeny.  Zmiany w tych funkcjach nie podlegają kontroli systemu transakcji. W związku z tym nie trzeba aktualizować ich przy użyciu reguł, ponieważ reguły nie są wywoływane, gdy użytkownik wykonuje polecenie Cofnij.

Zamiast tego można zaktualizować takie funkcje przy użyciu <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. W poniższym przykładzie styl strzałki łącznika jest kontrolowany przez wartość właściwości domeny w relacji, która jest wyświetlana przez łącznik:

```csharp
public partial class ArrowConnector // My connector class.
{
    /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape's built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }

    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}
```

`AssociateValueWith()` należy wywoływać jednokrotnie dla każdej właściwości domeny, która ma zostać zarejestrowana. Po jego wywołaniu wszelkie zmiany określonej właściwości będą wywoływać `OnAssociatedPropertyChanged()` w dowolnych kształtach, które zawierają element modelu właściwości.

Nie jest konieczne wywoływanie `AssociateValueWith()` dla każdego wystąpienia. Chociaż InitializeResources jest metodą wystąpienia, jest wywoływana tylko raz dla każdej klasy kształtu.
