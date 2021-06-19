---
title: Aktualizowanie kształtów i łączników, aby odzwierciedlały model
description: Dowiedz się, że w języku specyficznym dla Visual Studio, wygląd kształtu może odzwierciedlać stan modelu bazowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6439a01de2a02361914ce227c43d903f1b24b405
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388571"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Aktualizowanie kształtów i łączników, aby odzwierciedlały model

W języku specyficznym dla Visual Studio można sprawić, że wygląd kształtu będzie odzwierciedlał stan modelu bazowego.

Przykłady kodu w tym temacie należy dodać do `.cs` pliku w `Dsl` projekcie. Te dyrektywy są potrzebne w każdym pliku:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Ustawianie właściwości mapy kształtów w celu kontrolowania widoczności dekoratora

Widoczność dekoratora można kontrolować bez pisania kodu programu, konfigurując mapowanie między kształtem a klasą domeny w definicji DSL. Aby uzyskać więcej informacji, [zobacz How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Uwidocznij kolor i styl kształtu jako właściwości

W definicji DSL kliknij prawym przyciskiem myszy klasę kształtu, wskaż polecenie **Dodaj** ujawnione , a następnie kliknij jeden z elementów, taki jak Fill Color ( **Kolor wypełnienia).**

Kształt ma teraz właściwość domeny, która można ustawić w kodzie programu lub jako użytkownik. Aby na przykład ustawić go w kodzie programu polecenia lub reguły, możesz napisać:

`shape.FillColor = System.Drawing.Color.Red;`

Jeśli chcesz, aby zmienna właściwości była tylko pod kontrolą programu, a nie przez użytkownika, wybierz nową właściwość domeny, taką jak **Kolor** wypełnienia na diagramie definicji DSL. Następnie w okno Właściwości dla ustawienia **Można** przeglądać ustawić wartość lub Jest tylko do odczytu `false` **interfejsu użytkownika na** wartość `true` .

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definiowanie reguł zmiany, aby kolor, styl lub lokalizacja zależeć od właściwości elementu modelu
 Można zdefiniować reguły, które aktualizują wygląd kształtu w zależności od innych części modelu. Można na przykład zdefiniować regułę zmiany dla elementu modelu, która aktualizuje kolor jego kształtu w zależności od właściwości elementu modelu. Aby uzyskać więcej informacji na temat reguł zmiany, [zobacz Reguły propagacji zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

 Reguł należy używać tylko do aktualizowania właściwości, które są przechowywane w magazynie, ponieważ reguły nie są wywoływane podczas wykonania polecenia Cofnij. Nie obejmuje to niektórych funkcji graficznych, takich jak rozmiar i widoczność kształtu. Aby zaktualizować te funkcje kształtu, zobacz Aktualizowanie funkcji graficznych bez [magazynu.](#OnAssociatedProperty)

 W poniższym przykładzie przyjęto założenie, że użytkownik został ujawniony jako właściwość domeny zgodnie z `FillColor` opisem w poprzedniej sekcji.

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

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Inicjowanie właściwości kształtu za pomocą właściwości OnChildConfigured

Aby ustawić właściwości kształtu podczas jego tworzenia po raz pierwszy, przesłonięcie `OnChildConfigured()` w częściowej definicji klasy diagramu. Klasa diagramu jest określona w definicji DSL, a wygenerowany kod znajduje się w **pliku Dsl\Generated Code\Diagram.cs.** Na przykład:

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

Tej metody można używać zarówno dla właściwości domeny, jak i funkcji niechowających się w magazynie, takich jak rozmiar kształtu.

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> Aktualizowanie innych funkcji kształtu za pomocą funkcji AssociateValueWith()

W przypadku niektórych funkcji kształtu, takich jak w tle lub styl strzałki łącznika, nie ma wbudowanej metody uwyłania tej funkcji jako właściwości domeny.  Zmiany w takich funkcjach nie są pod kontrolą systemu transakcji. W związku z tym nie jest odpowiednie zaktualizowanie ich przy użyciu reguł, ponieważ reguły nie są wywoływane, gdy użytkownik wykonuje polecenie Cofnij.

Zamiast tego można zaktualizować takie funkcje przy użyciu programu <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> . W poniższym przykładzie styl strzałki łącznika jest kontrolowany przez wartość właściwości domeny w relacji, która jest wyświetlana przez łącznik:

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

`AssociateValueWith()` powinien być wywoływany jeden raz dla każdej właściwości domeny, która ma zostać zarejestrowana. Po jego wywołaniu wszelkie zmiany określonej właściwości będą wywoływane w dowolnych kształtach, `OnAssociatedPropertyChanged()` które prezentują element modelu właściwości.

Wywołanie wywołania dla `AssociateValueWith()` każdego wystąpienia nie jest konieczne. Mimo że InitializeResources jest metodą wystąpienia, jest wywoływana tylko raz dla każdej klasy kształtu.
