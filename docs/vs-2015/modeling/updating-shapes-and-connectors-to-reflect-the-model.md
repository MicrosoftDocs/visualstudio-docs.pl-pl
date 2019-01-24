---
title: Aktualizowanie kształtów i łączników, aby odzwierciedlały Model | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e5c03fa6a04abd06af9e24b83977d491e9809265
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798867"
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Aktualizowanie kształtów i łączników, aby odzwierciedlały model
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W języku specyficznym dla domeny, w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], możesz wprowadzić wygląd kształtu odzwierciedlają stan odpowiedni model.  
  
 Przykłady kodu, w tym temacie, powinny zostać dodane do `.cs` plików w Twojej `Dsl` projektu. Te instrukcje w każdym pliku będą potrzebne:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Ustaw właściwości mapowanie kształtów w celu kontrolowania widoczności elementu decorator  
 Można kontrolować widoczność dekoratora, bez konieczności pisania kodu programu, konfigurując mapowanie między kształtem i klasy domeny w definicji DSL. Więcej informacji znajduje się w następujących tematach:  
  
-   [Instrukcje: Kontrolowanie widoczności elementu Decorator — przekierowanie](../misc/how-to-control-the-visibility-of-a-decorator-redirect.md)  
  
-   [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)  
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Uwidacznianie kolor i Styl kształtu jako właściwości  
 W definicji DSL, kliknij prawym przyciskiem myszy kształt klasy, wskaż opcję **Dodaj udostępniane**, a następnie kliknij przycisk jednego z elementów takich jak **kolor wypełnienia**.  
  
 Kształt ma teraz właściwość domeny, którego można ustawić w kodzie programu, ani jako użytkownik. Na przykład aby ustawić go w kodzie programu, polecenia lub reguły, można napisać:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Jeśli chcesz, ustaw dla zmiennej właściwość tylko pod kontrolą programu, a nie przez użytkownika, wybierz nową właściwość domeny takie jak **kolor wypełnienia** w diagramem definicji DSL. Następnie w oknie właściwości ustaw **jest możliwa do przeglądania** do `false` lub ustaw **jest tylko do odczytu w interfejsie użytkownika** do `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Zdefiniuj reguły zmianę koloru, stylu lub lokalizacji, które są zależne od właściwości elementu modelu  
 Można zdefiniować reguły, które aktualizują wygląd kształtu zależne od innych części modelu. Na przykład można zdefiniować reguły zmian dla elementu modelu, który aktualizuje kolor jego kształt, które są zależne od właściwości elementu modelu. Aby uzyskać więcej informacji na temat zmiany reguł zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Zasady należy używać tylko po to, aby zaktualizować właściwości, które są obsługiwane w ramach Store, ponieważ zasady nie są wywoływane, gdy przeprowadzane jest polecenia Cofnij. Nie dotyczy to niektóre funkcje graficzne, takich jak rozmiar i widoczność kształtu. Aby zaktualizować te funkcje kształtu, zobacz [funkcji aktualizowania graficznych Non-Store](#OnAssociatedProperty).  
  
 W poniższym przykładzie założono, że są dostępne `FillColor` jako właściwość domeny, zgodnie z opisem w poprzedniej sekcji.  
  
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
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Użyj OnChildConfigured można zainicjować właściwości kształtu  
 Można ustawić właściwości kształtu, gdy po raz pierwszy utworzony, zastąpienie `OnChildConfigured()` w częściową definicję klasy diagramu. Klasa diagram jest określona w definicji DSL i wygenerowany kod znajduje się w **Dsl\Generated Code\Diagram.cs**. Na przykład:  
  
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
  
 Ta metoda może służyć zarówno dla właściwości domeny i funkcje-store, takie jak rozmiar kształtu.  
  
##  <a name="OnAssociatedProperty"></a> Użyj AssociateValueWith(), aby zaktualizować inne funkcje kształtu  
 W przypadku niektórych funkcji kształtu, takie jak czy ma cień lub Styl strzałki łącznika nie istnieje metoda wbudowanych ujawnienia funkcji jako właściwość domeny.  Zmiany tych funkcji nie są pod kontrolą systemu transakcji. W związku z tym, nie jest właściwe je zaktualizować przy użyciu reguł, ponieważ zasady nie są wywoływane, gdy użytkownik wykonuje polecenie Undo.  
  
 Zamiast tego można zaktualizować takich funkcji przy użyciu <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. W poniższym przykładzie Styl strzałki łącznika jest kontrolowany za pomocą wartości właściwości domeny w relacji, która wyświetla łącznika:  
  
```  
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
        { // Update the shape’s built-in Decorator feature:  
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
  
 `AssociateValueWith()` powinna być wywoływana jeden raz dla każdej właściwości domeny, który chcesz zarejestrować. Po jej wywołaniu, zmiany wprowadzone w określonej właściwości wywoła `OnAssociatedPropertyChanged()` w kształtów, które są dostępne właściwości elementu modelu.  
  
 Nie jest konieczne wywołać `AssociateValueWith()` dla każdego wystąpienia. Mimo że InitializeResources jest metodą wystąpienia, jest wywoływana tylko raz dla każdej klasy kształtu.
