---
title: 'Porady: przechwytywanie kliknięć w kształcie lub elemencie Decorator'
description: Dowiedz się, jak przechwycić kliknięcie kształtu lub dekoratora ikon oraz jak przechwytywać kliknięcia, dwukrotne kliknięcia, przeciąganie i inne gesty.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d2bcc16a6f2be70ae9ba0bfec0f3a24c94213dcf
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387167"
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>Porady: przechwytywanie kliknięć w kształcie lub elemencie Decorator
Poniższe procedury pokazują, jak przechwycić kliknięcie kształtu lub dekoratora ikon. Możesz przechwytywać kliknięcia, dwukrotne kliknięcia, przeciąganie i inne gesty, aby element odpowiadał.

## <a name="to-intercept-clicks-on-shapes"></a>Przechwytywanie kliknięć kształtów
 W projekcie Dsl w pliku kodu, który jest oddzielony od wygenerowanych plików kodu, napisz częściową definicję klasy dla klasy kształtu. Zastąp `OnDoubleClick()` lub jedną z innych metod o nazwie rozpoczynającej się od `On...` . Na przykład:

```csharp
public partial class MyShape // change
  {
    public override void OnDoubleClick(DiagramPointEventArgs e)
    {
      base.OnDoubleClick(e);
      System.Windows.Forms.MessageBox.Show("Click");
      e.Handled = true;
  }  }
```

> [!NOTE]
> Ustaw `e.Handled` wartość , chyba że `true` chcesz, aby zdarzenie zostało przekazane do zawierającego kształtu lub diagramu.

## <a name="to-intercept-clicks-on-decorators"></a>Przechwytywanie kliknięć w dekoratorach
 Dekoratory obrazów są wykonywane na wystąpieniu klasy ImageField, która ma metodę OnDoubleClick. Możesz przechwycić kliknięcia, jeśli napiszesz podklasę ImageField. Pola są ustawiane w metodzie InitializeShapeFields. W związku z tym należy zmienić tę metodę, aby utworzyć wystąpienia podklasy zamiast zwykłego ImageField. Metoda InitializeShapeFields znajduje się w wygenerowanym kodzie klasy shape. Klasę kształtu można przesłonić, jeśli ustawisz jej właściwość zgodnie `Generates Double Derived` z opisem w poniższej procedurze.

 Mimo że InitializeShapeFields jest metodą wystąpienia, jest wywoływana tylko raz dla każdej klasy. W związku z tym dla każdego pola w każdej klasie istnieje tylko jedno wystąpienie obiektu ClickableImageField, a nie jedno wystąpienie dla każdego kształtu na diagramie. Gdy użytkownik kliknie dwukrotnie wystąpienie, musisz zidentyfikować, które wystąpienie zostało trafione, jak pokazano w przykładzie.

#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>Aby przechwycić kliknięcie ikoną decorator

1. Otwórz lub utwórz rozwiązanie DSL.

2. Wybierz lub utwórz kształt, który ma dekorator ikon, i zamapuj go na klasę domeny.

3. W pliku kodu, który jest oddzielony od plików w folderze, utwórz nową podklasę `GeneratedCode` ImageField:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using System.Collections.Generic;
    using System.Linq;

    namespace Fabrikam.MyDsl { // Change to your namespace
    internal class ClickableImageField : ImageField
    {
      // You can also override OnClick and so on.
      public override void OnDoubleClick(DiagramPointEventArgs e)
      {
        base.OnDoubleClick(e);
        // Work out which instance was hit.
        MyShape shapeHit = e.HitDiagramItem.Shape as MyShape;
        if (shapeHit != null)
        {
          MyDomainClass element =
              shapeHit.ModelElement as MyDomainClass;
          System.Windows.Forms.MessageBox.Show(
             "Double click on shape for " + element.Name);
          // If we do not set Handled, the event will
          // be passed to the containing shape:
          e.Handled = true;
        }
      }

       public ClickableImageField(string fieldName)
         : base(fieldName)
       { }
    }
    ```

     Należy ustawić wartość Handled na true, jeśli nie chcesz, aby zdarzenie było przekazywane do zawierającego kształtu.

4. Zastąp metodę InitializeShapeFields w klasie kształtu, dodając następującą definicję klasy częściowej.

    ```csharp
    public partial class MyShape // change
    {
     protected override void InitializeShapeFields
          (IList<ShapeField> shapeFields)
     {
      base.InitializeShapeFields(shapeFields);
      // You can see the above method in MyShapeBase
      // in the generated Shapes.cs
      // It has already added fields for the Icons.
      // So you will have to retrieve them and replace with your own.
      ShapeField unwantedField = shapeFields.First
          (field => field.Name == "IconDecorator1");
      shapeFields.Remove(unwantedField);

      // Now replicate the generated code from the base class
      // in Shape.cs, but with your own image constructor.
      ImageField field2 = new ClickableImageField("IconDecorator1");
      field2.DefaultImage = ImageHelper.GetImage(
        MyDslDomainModel.SingletonResourceManager
        .GetObject("MyShapeIconDecorator1DefaultImage"));
          shapeFields.Add(field2);
    }
    ```

1. Skompiluj i uruchom rozwiązanie.

2. Kliknij dwukrotnie ikonę wystąpienia kształtu. Powinien zostać wyświetlony komunikat testowy.

## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>Przechwytywanie kliknięć i przeciągania na listach CompartmentShape
 Poniższy przykład umożliwia użytkownikom ponowne uporządkowanie elementów w kształcie przedziału przez przeciągnięcie ich. Aby uruchomić ten kod:

1. Utwórz nowe rozwiązanie DSL przy użyciu szablonu **rozwiązania Diagramy** klas.

    Możesz również pracować z własnym rozwiązaniem, które zawiera kształty przedziałów. W tym kodzie przyjęto założenie, że istnieje relacja osadzania między elementami modelu reprezentowanymi przez kształt i elementami reprezentowanymi w elementach listy przedziałów.

2. Ustaw właściwość **Generates Double Derived kształtu** przedziału.

3. Dodaj ten kod w pliku w **projekcie Dsl.**

4. Dostosuj nazwy klas domen i kształtu w tym kodzie, aby dopasować je do własnego DSL.

   Podsumowując, kod działa w następujący sposób. W tym przykładzie `ClassShape` jest nazwą kształtu przedziału.

- Zestaw programów obsługi zdarzeń myszy jest dołączany do każdego wystąpienia przedziału podczas jego tworzenia.

- Zdarzenie `ClassShape.MouseDown` przechowuje bieżący element.

- Gdy mysz przesuwa się poza bieżący element, tworzone jest wystąpienie elementu MouseAction, które ustawia kursor i przechwytuje wskaźnik myszy do momentu jego zwolnieniu.

     Aby uniknąć zakłócania innych akcji myszy, takich jak zaznaczanie tekstu elementu, akcja MouseAction nie zostanie utworzona, dopóki mysz nie opuści oryginalnego elementu.

     Alternatywą dla tworzenia akcji MouseAction jest po prostu nasłuchiwać funkcji MouseUp. Jednak nie będzie to działać prawidłowo, jeśli użytkownik zwolni mysz po przeciągnięciu jej poza przedział. Akcja MouseAction jest w stanie wykonać odpowiednią akcję niezależnie od tego, gdzie jest zwolniona mysz.

- Po zwolnieniu myszy mouseAction.MouseUp zmienia kolejność połączeń między elementami modelu.

- Zmiana kolejności ról jest wyzjemnia regułę, która aktualizuje wyświetlanie. To zachowanie jest już zdefiniowane i nie jest wymagany żaden dodatkowy kod.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Design;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Collections.Generic;
using System.Linq;

// This sample allows users to re-order items in a compartment shape by dragging.

// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).
// You will need to change the following domain class names to your own:
// ClassShape = a compartment shape
// ClassModelElement = the domain class displayed using a ClassShape
// This code assumes that the embedding relationships
// displayed in the compartments don't use inheritance
// (don't have base or derived domain relationships).

namespace Company.CompartmentDrag
{
 /// <summary>
 /// Manage the mouse while dragging a compartment item.
 /// </summary>
 public class CompartmentDragMouseAction : MouseAction
 {
  private ModelElement sourceChild;
  private ClassShape sourceShape;
  private RectangleD sourceCompartmentBounds;

  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)
   : base (sourceParentShape.Diagram)
  {
   sourceChild = sourceChildElement;
   sourceShape = sourceParentShape;
   sourceCompartmentBounds = bounds; // For cursor.
  }

  /// <summary>
  /// Call back to the source shape to drop the dragged item.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   sourceShape.DoMouseUp(sourceChild, e);
   this.Cancel(e.DiagramClientView);
   e.Handled = true;
  }

  /// <summary>
  /// Ideally, this shouldn't happen. This action should only be active
  /// while the mouse is still pressed. However, it can happen if you
  /// move the mouse rapidly out of the source shape, let go, and then
  /// click somewhere else in the source shape.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseDown(DiagramMouseEventArgs e)
  {
   base.OnMouseDown(e);
   this.Cancel(e.DiagramClientView);
   e.Handled = false;
  }

  /// <summary>
  /// Display an appropriate cursor while the drag is in progress:
  /// Up-down arrow if we are inside the original compartment.
  /// No entry if we are elsewhere.
  /// </summary>
  /// <param name="currentCursor"></param>
  /// <param name="diagramClientView"></param>
  /// <param name="mousePosition"></param>
  /// <returns></returns>
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)
  {
   // If the cursor is inside the original compartment, show up-down cursor.
   return sourceCompartmentBounds.Contains(mousePosition)
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.
    : System.Windows.Forms.Cursors.No;
  }
 }

 /// <summary>
 /// Override some methods of the compartment shape.
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****
 /// </summary>
 public partial class ClassShape
 {
  /// <summary>
  /// Model element that is being dragged.
  /// </summary>
  private static ClassModelElement dragStartElement = null;
  /// <summary>
  /// Absolute bounds of the compartment, used to set the cursor.
  /// </summary>
  private static RectangleD compartmentBounds;

  /// <summary>
  /// Attach mouse listeners to the compartments for the shape.
  /// This is called once per compartment shape.
  /// The base method creates the compartments for this shape.
  /// </summary>
  public override void EnsureCompartments()
  {
   base.EnsureCompartments();
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())
   {
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);
   }
  }

  /// <summary>
  /// Remember which item the mouse was dragged from.
  /// We don't create an Action immediately, as this would inhibit the
  /// inline text editing feature. Instead, we just remember the details
  /// and will create an Action when/if the mouse moves off this list item.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)
  {
   dragStartElement = e.HitDiagramItem.RepresentedElements
     .OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item,
  /// but still inside the compartment, create an Action
  /// to supervise the cursor and handle subsequent mouse events.
  /// Transfer the details of the initial mouse position to the Action.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)
  {
   if (dragStartElement != null)
   {
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())
    {
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);
     dragStartElement = null;
    }
   }
  }

  /// <summary>
  /// User has released the mouse button.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)
  {
    dragStartElement = null;
  }

  /// <summary>
  /// Forget the source item if mouse up occurs outside the
  /// compartment.
  /// </summary>
  /// <param name="e"></param>
  public override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   dragStartElement = null;
  }

  /// <summary>
  /// Called by the Action when the user releases the mouse.
  /// If we are still on the same compartment but in a different list item,
  /// move the starting item to the position of the current one.
  /// </summary>
  /// <param name="dragFrom"></param>
  /// <param name="e"></param>
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)
  {
   // Original or "from" item:
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;
   // Current or "to" item:
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   if (dragFromElement != null && dragToElement != null)
   {
    // Find the common parent model element, and the relationship links:
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)
    {
     // Get the static relationship and role (= end of relationship):
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];
     // Get the node in which the element is embedded, usually the element displayed in the shape:
     ModelElement parentFrom = parentFromLink.LinkedElements[0];

     // Same again for the target:
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];
     ModelElement parentTo = parentToLink.LinkedElements[0];

     // Mouse went down and up in same parent and same compartment:
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)
     {
      // Find index of target position:
      int newIndex = 0;
      var elementLinks = parentToRole.GetElementLinks(parentTo);
      foreach (ElementLink link in elementLinks)
      {
       if (link == parentToLink) { break; }
       newIndex++;
      }

      if (newIndex < elementLinks.Count)
      {
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))
       {
        parentFromLink.MoveToIndex(parentFromRole, newIndex);
        t.Commit();
       }
      }
     }
    }
   }
  }

  /// <summary>
  /// Get the embedding link to this element.
  /// Assumes there is no inheritance between embedding relationships.
  /// (If there is, you need to make sure you've got the relationship
  /// that is represented in the shape compartment.)
  /// </summary>
  /// <param name="child"></param>
  /// <returns></returns>
  ElementLink GetEmbeddingLink(ClassModelElement child)
  {
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)
   {
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))
    {
     // Just the assume the first embedding link is the only one.
     // Not a valid assumption if one relationship is derived from another.
     return link;
    }
   }
   return null;
  }
 }
}
```

## <a name="see-also"></a>Zobacz też

- [Odpowiadanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)
- [Właściwości elementów Decorator](../modeling/properties-of-decorators.md)
