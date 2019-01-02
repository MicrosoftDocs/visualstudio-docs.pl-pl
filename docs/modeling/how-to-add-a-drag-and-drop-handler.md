---
title: 'Instrukcje: Dodawanie obsługi przeciągania i upuszczania'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 90385b233e859bf1cdd8ea1617b94efe58ec4cbf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876396"
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>Instrukcje: Dodawanie obsługi przeciągania i upuszczania

Tak, aby użytkownicy można przeciągnąć elementy na diagramie z innymi diagramami lub z innych części programu Visual Studio, można dodać do DSL, obsługi przeciągania i upuszczania. Można również dodać procedury obsługi dla zdarzenia takie jak kliknie dwukrotnie. Razem obsługi przeciągania i upuszczania i kliknij dwukrotnie plik, są znane jako *procedury obsługi gestów*.

W tym temacie omówiono gestów przeciągania i upuszczania, które pochodzą na inne diagramy. Przenoszenie i kopiowanie zdarzenia w obrębie jednego diagramu, należy wziąć pod uwagę alternatywne Definiowanie podklasą `ElementOperations`. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md). Można również dostosować definicji DSL.

## <a name="defining-gesture-handlers-by-overriding-shapeelement-methods"></a>Definiowanie procedury obsługi gestu przez zastąpienie metody ShapeElement

`OnDragDrop`, `OnDoubleClick`, `OnDragOver`, i innych metod, które mogą zostać przesłonięte.

Dodaj nowy plik kodu do projektu DSL. W przypadku obsługi gestu można zwykle musi mieć co najmniej następujące `using` instrukcji:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Linq;
```

W nowym pliku należy zdefiniować klasę częściową dla kształt lub diagram klasy, które powinno odpowiedzieć na operacji przeciągania. Należy zastąpić następujące metody:

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>— Ta metoda jest wywoływana, gdy wskaźnik myszy zostanie kształtu w czasie trwania operacji przeciągania. Metoda należy sprawdzić element, który użytkownik przeciąga i ustaw właściwość efekt, aby wskazać, czy użytkownika można upuścić elementu w tego kształtu. Właściwości efektu określa wygląd kursor znajduje się nad tym kształtem i określa również, czy `OnDragDrop()` zostanie wywołana, gdy użytkownik zwolni przycisk myszy.

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

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> — Ta metoda jest wywoływana, gdy użytkownik zwolni przycisk myszy, gdy wskaźnik myszy znajduje się nad tym kształt lub diagram, jeśli `OnDragOver(DiagramDragEventArgs e)` ustawione wcześniej `e.Effect` wartość inną niż `None`.

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

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> — Ta metoda jest wywoływana, gdy użytkownik kliknie dwukrotnie kształt lub diagram.

     Aby uzyskać więcej informacji, zobacz [jak: Przechwytywanie kliknięć w kształcie lub elemencie Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Zdefiniuj `IsAcceptableDropItem(e)` Aby ustalić, czy jest dopuszczalne przeciąganego elementu i ProcessDragDropItem(e) aktualizacji modelu, gdy element zostanie porzucony. Te metody należy najpierw wyodrębnić elementu na podstawie argumentów zdarzeń. Aby uzyskać informacje o tym, jak to zrobić, zobacz [jak odwołać się do przeciągniętego elementu](#extracting).

## <a name="define-gesture-handlers-by-using-mef"></a>Definiowanie procedury obsługi gestu za pomocą MEF

Użyj tej metody, jeśli chcesz, aby deweloperów innych firm, aby można było zdefiniować własne programy obsługi DSL. Użytkowników można zainstalować rozszerzenia innych firm, po nich zainstalować DSL.

MEF (Managed Extensibility Framework) pozwala zdefiniować składniki, które mogą być instalowane z minimalną konfiguracją. Aby uzyskać więcej informacji, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-define-a-mef-gesture-handler"></a>Do definiowania obsługi gestu MEF

1.  Dodaj do swojej **Dsl** i **DslPackage** projektów **MefExtension** pliki, które są opisane w [rozszerzanie DSL za pomocą MEF](../modeling/extend-your-dsl-by-using-mef.md).

2.  Jest dostępna możliwość definiowania obsługi gestu jako składnik MEF:

    ```csharp
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

     Można utworzyć więcej niż jeden składnik obsługi gestu, np. gdy ma różne typy obiektów przeciąganego.

3.  Dodaj częściowych definicji klasy dla kształtu docelowego, łącznika lub diagram klas i definiować metody `IsAcceptableDropItem()` i `ProcessDragDropItem()`. Te metody musi rozpoczynać się przez wyodrębnienie przeciąganego elementu z argumentów zdarzenia. Aby uzyskać więcej informacji, zobacz [jak odwołać się do przeciągniętego elementu](#extracting).

## <a name="how-to-decode-the-dragged-item"></a>Sposób dekodowania przeciąganego elementu

Elementy można przeciągać z dowolnym oknie lub na pulpicie, a także z języka DSL.

Gdy użytkownik przeciąga element na diagramie lub z jednej części diagramu do innego, jest dostępna w informacje na temat elementu, który jest przeciągany `DiagramDragEventArgs`. Ponieważ można mieć rozpocząć operacji przeciągania u dowolnego obiektu na ekranie, dane mogą być dostępne w jednym z różnych formatach. Twój kod musi rozpoznać formatów, z którymi jest przystosowana do uwzględniania.

Aby odnaleźć formaty, w których jest dostępne informacje o źródle przeciągania, uruchomić kod w tryb debugowania, ustawienie punktu przerwania na wpis, aby `OnDragOver()` lub `CanDragDrop()`. Sprawdź wartości `DiagramDragEventArgs` parametru. Informacje są udostępniane w dwóch formach:

-   <xref:System.Windows.Forms.IDataObject>  `Data` — W tym właściwości niesie ze sobą wersje serializacji obiektów źródłowych zwykle w wielu formatach. Są najbardziej przydatne funkcje:

    -   diagramEventArgs.Data.GetDataFormats() — zawiera listę formatów, w których mogą dekodować przeciągany obiekt. Na przykład, jeśli użytkownik przeciąga pliku z pulpitu, dostępne formaty obejmują nazwę pliku ("`FileNameW`").

    -   `diagramEventArgs.Data.GetData(format)` -Dekoduje przeciągany obiekt w określonym formacie. Obiekt do odpowiedniego typu rzutowania. Na przykład:

         `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`

         Obiekty, takie jak odwołania do magistrali modelu ze źródła mogą również przesyłać w format niestandardowy. Aby uzyskać więcej informacji, zobacz [sposób wysyłania magistrali odwołania do modelu w operacji przeciągania i upuszczania](#mbr).

-   <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> `Prototype` — Użyj tej właściwości, jeśli użytkownicy mają przeciągnij elementy z języka DSL lub modelu UML. Element grupy prototypu zawiera jeden lub więcej obiektów, łączy i ich wartości właściwości. Służy również wklejanie i kiedy dodajesz element z przybornika. W prototyp obiektów i ich typy są identyfikowane przez identyfikator Guid. Na przykład ten kod umożliwia użytkownikowi przenoszenie elementów klas z Eksploratora modelu UML lub diagramu UML:

    ```csharp
    private bool IsAcceptableDropItem(DiagramDragEventArgs e)
    {
      return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>
            element.DomainClassId.ToString()
            == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.
     // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId
    }
    ```

     Aby zaakceptować kształtów UML, należy określić identyfikator GUID w faktycznej klasy UML kształtu, eksperymentu. Pamiętaj, że zwykle ma więcej niż jeden typ elementu na dowolny diagram. Należy pamiętać, że obiekt przeciągnięte z diagram DSL lub UML jest kształtu, a nie do elementu modelu.

`DiagramDragEventArgs` ma również właściwości, które wskazują bieżącej pozycji wskaźnika myszy i tego, czy użytkownik jest naciśnięcie klawisza CTRL, ALT lub klawisze SHIFT.

## <a name="how-to-get-the-original-of-a-dragged-element"></a>Jak uzyskać oryginalną przeciąganego elementu

Jeśli przeciąganego elementu jest elementem DSL, możesz otworzyć model źródłowy i dostęp do elementu.

`Data` i `Prototype` właściwości argumentów zdarzenia zawiera tylko odwołanie do przeciągniętego kształtu. Zwykle Jeśli chcesz utworzyć obiekt w obiekcie docelowym DSL, który jest tworzony na podstawie prototypu w jakiś sposób, należy uzyskać dostęp do oryginalnego, na przykład odczytywać zawartość pliku lub przechodząc do elementu modelu, reprezentowane przez kształty. Aby to ułatwić, można użyć programu Visual Studio Model Bus.

### <a name="to-prepare-a-dsl-project-for-model-bus"></a>Aby przygotować projektu DSL Model Bus

1.  Udostępnić źródła DSL przez magistralę modelu w usłudze Visual Studio:

    1.  Pobierz i zainstaluj rozszerzenie programu Visual Studio Model Bus, jeśli nie jest już zainstalowany. Aby uzyskać więcej informacji, zobacz [wizualizacji i modelowania SDK](http://go.microsoft.com/fwlink/?LinkID=185579).

    2.  Otwórz plik definicji DSL źródła DSL w projektanta DSL. Kliknij prawym przyciskiem myszy powierzchnię projektu, a następnie kliknij przycisk **Włącz Modelbus**. W oknie dialogowym wybierz jedną lub obie opcje.  Kliknij przycisk **OK**. Nowy projekt "ModelBus" jest dodawany do rozwiązania DSL.

    3.  Kliknij przycisk **Przekształć wszystkie szablony** i ponownie skompiluj rozwiązanie.

### <a name="to-send-an-object-from-a-source-dsl"></a>Aby wysłać obiekt ze źródła DSL

1.  W swojej podklasy ElementOperations zastąpienia `Copy()` tak, aby go koduje odwołanie magistrali modelu (MBR) w IDataObject. Ta metoda zostanie wywołana, gdy użytkownik uruchamia przeciągnij z diagramu źródłowego. Zakodowany MBR następnie będą dostępne w IDataObject, gdy użytkownik porzuca w docelowym diagramie.

    ```csharp
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

### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>Aby odbierać odwołanie magistrali modelu z DSL w projekcie języka DSL lub UML docelowej

1.  W projekcie DSL docelowej należy dodać odwołania do projektu:

    -   Projekt źródła Dsl.

    -   Projekt źródła ModelBus.

2.  W pliku kodu programu obsługi gestu Dodaj następujące odwołania do przestrzeni nazw:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Integration;
    using SourceDslNamespace;
    using SourceDslNamespace.ModelBusAdapters;
    ```

3.  Poniższy przykład ilustruje sposób uzyskania dostępu do elementu modelu źródła:

    ```csharp
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

### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>Aby zaakceptować elementu Źródło modelu UML

-   Poniższy przykładowy kod przyjmuje obiekt pochodzącej z diagramu UML.

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

## <a name="using-mouse-actions-dragging-compartment-items"></a>Za pomocą akcji myszy: Przeciąganie elementów na przedział

Można napisać program obsługi, który przechwytuje akcje myszy na pola kształtu. Poniższy przykład pozwala użytkownikowi na zmienianie kolejności elementów na przedział, przeciągając wskaźnik myszy.

Aby skompilować ten przykład, należy utworzyć rozwiązanie za pomocą **diagramów klas** szablonu rozwiązania. Dodawanie pliku z kodem i Dodaj następujący kod. Dostosuj przestrzeni nazw, aby być taka sama jak własne.

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

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md)
- [Wdrażanie rozwiązań dla języka specyficznego dla domeny](../modeling/deploying-domain-specific-language-solutions.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
