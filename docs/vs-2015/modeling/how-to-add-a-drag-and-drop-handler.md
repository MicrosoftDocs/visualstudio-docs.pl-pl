---
title: 'Instrukcje: Dodawanie obsługi przeciągania i upuszczania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 39ee88a0-85c3-485e-8c0a-d9644c6b25d9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3bbb4500eb4792f77a7011bd95dd06d05d0ff8d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850421"
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>Porady: dodawanie obsługi przeciągania i upuszczania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można dodać programy obsługi dla zdarzeń przeciągania i upuszczania do DSL, dzięki czemu użytkownicy mogą przeciągać elementy na diagram z innych diagramów lub z innych części [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Możesz również dodać procedury obsługi dla zdarzeń, takich jak podwójne kliknięcia. Jednocześnie programy obsługi przeciągania i upuszczania oraz podwójnego kliknięcia są znane jako *programy obsługi gestów*.

 W tym temacie omówiono gesty przeciągania i upuszczania, które pochodzą z innych diagramów. Dla zdarzeń przenoszenia i kopiowania w ramach jednego diagramu należy rozważyć alternatywę definiowania podklasy `ElementOperations`. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md). Możliwe jest również dostosowanie definicji DSL.

## <a name="in-this-topic"></a>W tym temacie

- Pierwsze dwie sekcje opisują alternatywne metody definiowania procedury obsługi gestu:

  - [Definiowanie obsługi gestów przez zastępowanie metod ShapeElement](#overrideShapeElement). `OnDragDrop`, `OnDoubleClick`, `OnDragOver`i innych metod można przesłonić.

  - [Definiowanie obsługi gestów przy użyciu MEF](#MEF). Użyj tej metody, jeśli chcesz, aby deweloperzy innych firm mogli definiować własne programy obsługi na potrzeby języka DSL. Użytkownicy mogą zdecydować się na zainstalowanie rozszerzeń innych firm po zainstalowaniu DSL.

- [Jak zdekodować przeciągany element](#extracting). Elementy można przeciągać z dowolnego okna lub z pulpitu, a także z poziomu DSL.

- [Jak uzyskać oryginalny przeciągany element](#getOriginal). Jeśli przeciągany element jest elementem DSL, można otworzyć Model źródłowy i uzyskać dostęp do elementu.

- [Korzystanie z akcji myszy: przeciąganie elementów przedziału](#mouseActions). Ten przykład pokazuje procedurę obsługi niższego poziomu, która przechwytuje akcje myszy w polach kształtu. W przykładzie można zmienić kolejność elementów w przedziale, przeciągając myszą.

## <a name="overrideShapeElement"></a>Definiowanie obsługi gestów przez zastąpienie metod ShapeElement
 Dodaj nowy plik kodu do projektu DSL. Dla programu obsługi gestu zazwyczaj muszą istnieć co najmniej następujące instrukcje `using`:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Linq;
```

 W nowym pliku Zdefiniuj klasę częściową klasy kształtu lub diagramu, która powinna reagować na operację przeciągania. Zastąp następujące metody:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>— ta metoda jest wywoływana, gdy wskaźnik myszy zostanie przesunięty do kształtu podczas operacji przeciągania. Metoda powinna sprawdzić element, który użytkownik przeciągnieł, i ustawić właściwość efekt, aby wskazać, czy użytkownik może upuścić element w tym kształcie. Właściwość Effect określa wygląd kursora nad tym kształtem, a także określa, czy `OnDragDrop()` będzie wywoływana, gdy użytkownik zwolni przycisk myszy.

  ```csharp
  partial class MyShape // MyShape generated from DSL Definition.
  {
      public override void OnDragOver(DiagramDragEventArgs e)
      {
        base.OnDragOver(e);
        if (e.Effect == System.Windows.Forms.DragDropEffects.None
             && IsAcceptableDropItem(e)) // To be defined
        {
          e.Effect = System.Windows.Forms.DragDropEffects.Copy;
        }
      }

  ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> — ta metoda jest wywoływana, gdy użytkownik zwolni przycisk myszy, podczas gdy wskaźnik myszy znajduje się nad tym kształtem lub diagramem, jeśli `OnDragOver(DiagramDragEventArgs e)` poprzednio ustawiony `e.Effect` na wartość inną niż `None`.

  ```csharp
  public override void OnDragDrop(DiagramDragEventArgs e)
      {
        if (!IsAcceptableDropItem(e))
        {
          base.OnDragDrop(e);
        }
        else
        { // Process the dragged item, for example merging a copy into the diagram
          ProcessDragDropItem(e); // To be defined
        }
      }

  ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> — ta metoda jest wywoływana po dwukrotnym kliknięciu kształtu lub diagramu przez użytkownika.

   Aby uzyskać więcej informacji, zobacz [How to: przechwycenie kliknięcia kształtu lub dekoratora](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

  Zdefiniuj `IsAcceptableDropItem(e)`, aby określić, czy przeciągany element jest akceptowalny, i ProcessDragDropItem (e), aby zaktualizować model, gdy element zostanie usunięty. Te metody muszą najpierw wyodrębnić element z argumentów zdarzenia. Aby uzyskać informacje o tym, jak to zrobić, zobacz [jak uzyskać odwołanie do przeciąganego elementu](#extracting).

## <a name="MEF"></a>Definiowanie obsługi gestów przy użyciu MEF
 MEF (Managed Extensibility Framework) umożliwia zdefiniowanie składników, które mogą być instalowane z minimalną konfiguracją. Aby uzyskać więcej informacji, zobacz [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).

#### <a name="to-define-a-mef-gesture-handler"></a>Aby zdefiniować procedurę obsługi gestu MEF

1. Dodaj do projektów **DSL** i **DslPackage** **, które** są opisane w rozbudowaniu [DSL przy użyciu MEF](../modeling/extend-your-dsl-by-using-mef.md).

2. Teraz można zdefiniować procedurę obsługi gestu jako składnik MEF:

    ```

    // This attribute is defined in the generated file
    // DslPackage\MefExtension\DesignerExtensionMetaDataAttribute.cs:
    [MyDslGestureExtension]
    public class MyGestureHandlerClassName : IGestureExtension
    {
      /// <summary>
      /// Called to determine whether a drag onto the diagram can be accepted.
      /// </summary>
      /// <param name="diagramDragEventArgs">Contains a link to the item that is being dragged</param>
      /// <param name="targetMergeElement">The shape or connector that the mouse is over</param>
      /// <returns>True if the item can be accepted on the targetMergeElement.</returns>
      public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null) return false;
        if (target.IsAcceptableDropItem(diagramDragEventArgs)) return true;
        return false;
      }
      public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null || ! target.IsAcceptableDropItem(diagramDragEventArgs)) return;
        // Process the dragged item, for example merging a copy into the diagram:
        target.ProcessDragDropItem(diagramDragEventArgs);
     }

    ```

     Można utworzyć więcej niż jeden składnik obsługi gestu, taki jak w przypadku różnych typów przeciąganych obiektów.

3. Dodaj definicje klas częściowych dla kształtu docelowego, łącznika lub klasy diagramu i zdefiniuj metody `IsAcceptableDropItem()` i `ProcessDragDropItem()`. Te metody muszą zaczynać się od wyodrębnienia przeciąganego elementu z argumentów zdarzenia. Aby uzyskać więcej informacji, zobacz [jak uzyskać odwołanie do przeciąganego elementu](#extracting).

## <a name="extracting"></a>Jak zdekodować przeciągany element
 Gdy użytkownik przeciągnie element na diagram lub z jednej części diagramu do innego, informacje o przeciąganym elemencie są dostępne w `DiagramDragEventArgs`. Ponieważ operacja przeciągania mogła rozpocząć się w dowolnym obiekcie na ekranie, dane mogą być dostępne w jednym z różnych formatów. Kod musi rozpoznawać formaty, z którymi może się kierować.

 Aby poznać formaty, w których dostępne są informacje źródłowe przeciągania, uruchom kod w trybie debugowania, ustawiając punkt przerwania w pozycji do `OnDragOver()` lub `CanDragDrop()`. Sprawdź wartości parametru `DiagramDragEventArgs`. Informacje są dostępne w dwóch formach:

- <xref:System.Windows.Forms.IDataObject>`Data` — ta właściwość przenosi serializowane wersje obiektów źródłowych, zwykle w więcej niż jednym formacie. Najbardziej przydatne funkcje to:

  - diagramEventArgs. Data. GetDataFormats () — wyświetla listę formatów, w których można zdekodować przeciągany obiekt. Na przykład jeśli użytkownik przeciągnie plik z pulpitu, dostępne są następujące formaty: nazwa pliku ("`FileNameW`").

  - `diagramEventArgs.Data.GetData(format)` — dekoduje przeciągany obiekt w określonym formacie. Rzutowanie obiektu na odpowiedni typ. Na przykład:

       `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`

       Możesz również przesyłać obiekty takie jak odwołania do magistrali modelu ze źródła we własnym formacie niestandardowym. Aby uzyskać więcej informacji, zobacz [jak wysyłać odwołania do magistrali modelu w przeciąganiu i upuszczaniu](#mbr).

- <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> `Prototype` — Użyj tej właściwości, jeśli chcesz, aby użytkownicy przeciągać elementy z modelu języka DSL lub UML. Prototyp grupy elementów zawiera co najmniej jeden obiekt, linki i ich wartości właściwości. Jest również używany w operacjach wklejania i podczas dodawania elementu z przybornika. W prototypie obiekty i ich typy są identyfikowane przez identyfikator GUID. Na przykład ten kod umożliwia użytkownikowi przeciąganie elementów klasy z diagramu UML lub Eksploratora modelu UML:

  ```csharp
  private bool IsAcceptableDropItem(DiagramDragEventArgs e)
  {
    return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>
          element.DomainClassId.ToString()
          == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.
   // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId
  }

  ```

   Aby zaakceptować kształty UML, ustal identyfikatory GUID klas kształtu UML przez eksperyment. Należy pamiętać, że na dowolnym diagramie jest zwykle więcej niż jeden typ elementu. Pamiętaj również, że obiekt przeciągany z diagramu DSL lub UML jest kształtem, a nie elementem modelu.

  `DiagramDragEventArgs` ma również właściwości, które wskazują bieżącą pozycję wskaźnika myszy i czy użytkownik naciska klawisze CTRL, ALT lub SHIFT.

## <a name="getOriginal"></a>Jak uzyskać oryginalny element przeciągany
 Właściwości `Data` i `Prototype` argumentów zdarzenia zawierają tylko odwołanie do przeciąganego kształtu. Zwykle, jeśli chcesz utworzyć obiekt w docelowym elemencie DSL, który jest wyprowadzany ze prototypu w jakiś sposób, musisz uzyskać dostęp do oryginału, na przykład odczytując zawartość pliku lub przechodząc do elementu modelu reprezentowanego przez kształt.  Do tego celu można użyć magistrali modelu programu Visual Studio.

### <a name="to-prepare-a-dsl-project-for-model-bus"></a>Aby przygotować projekt DSL dla magistrali modelu

1. Udostępnienie źródłowej magistrali DSL przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Model Bus:

    1. Pobierz i zainstaluj rozszerzenie magistrali modelu programu Visual Studio, jeśli nie jest jeszcze zainstalowane. Aby uzyskać więcej informacji, zobacz [wizualizacji i modelowania SDK](https://www.visualstudio.com/).

    2. Otwórz plik definicji DSL źródła DSL w projektant DSL. Kliknij prawym przyciskiem myszy powierzchnię projektu, a następnie kliknij przycisk **Włącz Modelbus**. W oknie dialogowym wybierz jedną lub obie opcje.  Kliknij przycisk **OK**. Do rozwiązania DSL zostanie dodany nowy projekt "ModelBus".

    3. Kliknij kolejno pozycje **Przekształć wszystkie szablony** i Skompiluj ponownie rozwiązanie.

### <a name="mbr"></a>Aby wysłać obiekt z źródłowego DSL

1. W podklasy ElementOperations Zastąp `Copy()` tak, aby zakodować odwołanie do magistrali modelu (MBR) do IDataObject. Ta metoda zostanie wywołana, gdy użytkownik rozpocznie przeciąganie z diagramu źródłowego. Zakodowany rekord MBR będzie dostępny w IDataObject, gdy użytkownik pospadnie na diagramie docelowym.

    ```

    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Shell;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Integration;
    using Microsoft.VisualStudio.Modeling.Integration.Shell;
    using System.Drawing; // PointF
    using  System.Collections.Generic; // ICollection
    using System.Windows.Forms; // for IDataObject
    ...
    public class MyElementOperations : DesignSurfaceElementOperations
    {
        public override void Copy(System.Windows.Forms.IDataObject data, System.Collections.Generic.ICollection<ModelElement> elements, ClosureType closureType, System.Drawing.PointF sourcePosition)
        {
          base.Copy(data, elements, closureType, sourcePosition);

          // Get the ModelBus service:
          IModelBus modelBus =
              this.Store.GetService(typeof(SModelBus)) as IModelBus;
          DocData docData = ((VSDiagramView)this.Diagram.ActiveDiagramView).DocData;
          string modelFile = docData.FileName;
          // Get an adapterManager for the target DSL:
          ModelBusAdapterManager manager =
              (modelBus.FindAdapterManagers(modelFile).First());
          ModelBusReference modelReference = manager.CreateReference(modelFile);
          ModelBusReference elementReference = null;
          using (ModelBusAdapter adapter = modelBus.CreateAdapter(modelReference))
          {
            elementReference = adapter.GetElementReference(elements.First());
          }

          data.SetData("ModelBusReference", elementReference);
        }
    ...}

    ```

### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>Aby odebrać odwołanie magistrali modelu z DSL w docelowym projekcie DSL lub UML

1. W docelowym projekcie DSL Dodaj odwołania do projektu do:

    - Źródłowy projekt DSL.

    - Źródłowy projekt ModelBus.

2. W pliku kodu obsługi gestów Dodaj następujące odwołania do przestrzeni nazw:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Integration;
    using SourceDslNamespace;
    using SourceDslNamespace.ModelBusAdapters;

    ```

3. Poniższy przykład ilustruje, jak uzyskać dostęp do źródłowego elementu modelu:

    ```
    partial class MyTargetShape // or diagram or connector
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
        // Verify that we're being passed an Object Shape.
        ElementGroupPrototype prototype = diagramDragEventArgs.Prototype;
        if (prototype == null) return;
        if (Company.InstanceDiagrams.ObjectShape.DomainClassId
          != prototype.RootProtoElements.First().DomainClassId)
          return;
        // - This is an ObjectShape.
        // - We need to access the originating Store, find the shape, and get its object.

        IModelBus modelBus = targetDropElement.Store.GetService(typeof(SModelBus)) as IModelBus;

        // Unpack the MBR that was packed in Copy:
        ModelBusReference reference = diagramDragEventArgs.Data.GetData("ModelBusReference") as ModelBusReference;
        using (SourceDslAdapter adapter = modelBus.CreateAdapter(reference) as SourceDslAdapter)
        {
          using (ILinkedUndoTransaction t = LinkedUndoContext.BeginTransaction("doing things"))
          {
            // Quickest way to get the shape from the MBR:
            ObjectShape firstShape = adapter.ResolveElementReference<ObjectShape>(reference);

            // But actually there might be several shapes - so get them from the prototype instead:
            IElementDirectory remoteDirectory = adapter.Store.ElementDirectory;
            foreach (Guid shapeGuid in prototype.SourceRootElementIds)
            {
              PresentationElement pe = remoteDirectory.FindElement(shapeGuid) as PresentationElement;
              if (pe == null) continue;
              SourceElement instance = pe.ModelElement as SourceElement;
              if (instance == null) continue;

              // Do something with the object:
          instance...
            }
            t.Commit();
          }
        }
    }

    ```

### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>Aby zaakceptować element pochodzący z modelu UML

- Poniższy przykład kodu akceptuje obiekt porzucony z diagramu UML.

    ```csharp

      using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
      using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
      using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
      using Microsoft.VisualStudio.Modeling;
      using Microsoft.VisualStudio.Modeling.Diagrams;
      using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
      using Microsoft.VisualStudio.Uml.Classes;
      using System;
      using System.ComponentModel.Composition;
      using System.Linq;
    ...
    partial class TargetShape
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
            EnvDTE.DTE dte = this.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
            // Find the UML project
            foreach (EnvDTE.Project project in dte.Solution.Projects)
            {
              IModelingProject modelingProject = project as IModelingProject;
              if (modelingProject == null) continue; // not a modeling project
              IModelStore store = modelingProject.Store;
              if (store == null) return;

              foreach (IDiagram dd in store.Diagrams())
              {
                  // Get Modeling.Diagram that implements UML.IDiagram:
                  Diagram diagram = dd.GetObject<Diagram>();

                  foreach (Guid elementId in e.Prototype.SourceRootElementIds)
                  {
                    ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
                    if (shape == null) continue;
                    // This example assumes the shape is a UML class:
                    IClass classElement = shape.ModelElement as IClass;
                    if (classElement == null) continue;

                    // Now do something with the UML class element ...
                  }
            }
          break; // don't try any more projects
    }  }  }

    ```

## <a name="mouseActions"></a>Korzystanie z akcji myszy: przeciąganie elementów przedziału
 Można napisać procedurę obsługi, która przechwytuje akcje myszy w polach kształtu. Poniższy przykład umożliwia użytkownikowi zmianę kolejności elementów w przedziale, przeciągając myszą.

 Aby skompilować ten przykład, Utwórz rozwiązanie przy użyciu szablonu rozwiązania **diagramy klas** . Dodaj plik kodu i Dodaj następujący kod. Dostosuj przestrzeń nazw tak, aby była taka sama jak własna.

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
// This code assumes that the embedding relationships displayed in the compartments
// don't use inheritance (don't have base or derived domain relationships).

namespace Company.CompartmentDrag  // EDIT.
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
  /// click somewhere else in the source shape. Yuk.
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
   dragStartElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item, but still inside the compartment,
  /// create an Action to supervise the cursor and handle subsequent mouse events.
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
 [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md) [wdrażanie rozwiązań języka właściwych dla domeny](../modeling/deploying-domain-specific-language-solutions.md)
