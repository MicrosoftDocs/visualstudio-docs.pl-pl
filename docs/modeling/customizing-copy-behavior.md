---
title: Dostosowywanie zachowania dotyczącego kopiowania
description: Dowiedz się, że w DSL utworzonym za pomocą Visual Studio SDK wizualizacji i modelowania możesz zmienić, co się stanie, gdy użytkownik kopiuje i wkleja elementy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c2e5ffbc7dde0bd1274756d1721088b18ea6ec34
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389413"
---
# <a name="customizing-copy-behavior"></a>Dostosowywanie zachowania dotyczącego kopiowania
W języku specyficznym dla domeny (DSL) utworzonym za pomocą zestawu VISUAL STUDIO Visualization and Modeling SDK można zmienić, co się stanie, gdy użytkownik kopiuje i wkleja elementy.

## <a name="standard-copy-and-paste-behavior"></a>Standardowe zachowanie podczas kopiowania i wklejania
 Aby włączyć kopiowanie, ustaw właściwość **Włącz wklejanie** kopii węzła **Edytor** w Eksploratorze DSL.

 Domyślnie, gdy użytkownik kopiuje elementy do schowka, kopiowane są również następujące elementy:

- Osadzone elementy potomne wybranych elementów. (Oznacza to, że elementy, które są elementami docelowymi osadzania relacji, które pochodzą ze skopiowanych elementów).

- Linki relacji między skopiowanym elementami.

  Ta reguła jest stosowana rekursywnie do skopiowanych elementów i linków.

  ![Skopiowane i wklejone elementy](../modeling/media/dslcopypastedefault.png)

  Skopiowane elementy i linki są serializowane i przechowywane w pliku <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), który znajduje się w schowku.

  Obraz skopiowanych elementów jest również umieszczany w schowku. Dzięki temu użytkownik może wkleić do innych aplikacji, takich jak Word.

  Użytkownik może wkleić skopiowane elementy do obiektu docelowego, który może akceptować elementy zgodnie z definicją DSL. Na przykład w DSL wygenerowanym na podstawie szablonu rozwiązania składników użytkownik może wkleić porty do składników, ale nie na diagramie; Elementy i mogą wklejać składniki na diagramie, ale nie do innych składników.

## <a name="customizing-copy-and-paste-behavior"></a>Dostosowywanie zachowania kopiowania i wklejania
 Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [Navigating and Updating a Model in Program Code (Nawigowanie i aktualizowanie modelu w kodzie programu).](../modeling/navigating-and-updating-a-model-in-program-code.md)

 **Włącza lub wyłącza kopiowanie, wycinanie i wklejanie.**
W Eksploratorze DSL ustaw właściwość **Włącz wklejanie** kopiowania węzła **Edytor.**

 **Skopiuj linki do tego samego obiektu docelowego.** Na przykład, aby skopiowane pole komentarza było połączone z tym samym elementem tematu.
Ustaw właściwość **Propagates Copy roli** na **Propagate copy (Propagacja kopii), aby połączyć tylko obiekt**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopiowania linków.](#customizeLinks)

 Kopiowanie połączonych elementów. Na przykład podczas kopiowania nowego elementu zostaną również wykonane kopie wszystkich połączonych pól komentarza.
Ustaw właściwość **Propagates Copy** roli na Propagate copy to link and opposite role player (Propagacja kopii w celu połączenia i **przeciwległego odtwarzacza roli).** Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopiowania linków.](#customizeLinks)

 **Szybkie duplikowanie elementów przez kopiowanie i wklejanie.** Zwykle skopiowany element jest nadal zaznaczony i nie można wkleić do niego tego samego typu elementu.
Dodaj dyrektywę Scalanie elementów do klasy domeny i ustaw ją w celu przekazywania scaleń do klasy nadrzędnej. Będzie to mieć taki sam wpływ na operacje przeciągania. Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przemieszczania elementów.](../modeling/customizing-element-creation-and-movement.md)

 \- lub —

 Wybierz diagram przed wklejenie elementów, przesłaniając element `ClipboardCommandSet.ProcessOnPasteCommand()` . Dodaj ten kod w pliku niestandardowym w projekcie DslPackage:

```csharp
namespace Company.MyDsl {
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
partial class MyDslClipboardCommandSet
{
  protected override void ProcessOnMenuPasteCommand()
  {
 // Deselect the current selection after copying:
 Diagram diagram = (this.CurrentModelingDocView as SingleDiagramDocView).Diagram;
    this.CurrentModelingDocView
     .SelectObjects(1, new object[] { diagram }, 0);
  }
} }
```

 **Utwórz dodatkowe linki, gdy użytkownik wkleja dane do wybranego obiektu docelowego.** Na przykład gdy pole komentarza jest wklejone do elementu, między nimi jest skojarzona relacja.
Dodaj dyrektywę scalania elementów do docelowej klasy domeny i ustaw ją w celu przetwarzania scalania przez dodanie linków. Będzie to mieć taki sam wpływ na operacje przeciągania. Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przemieszczania elementów.](../modeling/customizing-element-creation-and-movement.md)

 \- lub —

 Zastąp `ClipboardCommandSet.ProcessOnPasteCommand()` element , aby utworzyć dodatkowe linki po wywołaniu metody podstawowej.

 **Dostosuj formaty, w których elementy mogą** być kopiowane do aplikacji zewnętrznych — na przykład w celu dodania obramowania do formularza mapy bitowej.
Zastąp *mydsl* `ClipboardCommandSet.ProcessOnMenuCopyCommand()` w projekcie DslPackage.

 **Dostosuj sposób kopiowania elementów do schowka za pomocą polecenia kopiowania, ale nie w operacji przeciągania.**
Zastąp *mydsl* `ClipboardCommandSet.CopyModelElementsIntoElementGroupPrototype()` w projekcie DslPackage.

 **Zachowaj układ kształtu za pomocą kopiowania i wklejania.**
Gdy użytkownik kopiuje wiele kształtów, można zachować ich położenie względne, gdy są wklejone. Tę technikę zademonstrował przykład w [vmsdk: circuit diagrams sample](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8).

 Aby osiągnąć ten efekt, dodaj kształty i łączniki do skopiowanego elementu ElementGroupPrototype. Najbardziej wygodną metodą przesłonięcia jest elementOperations.CreateElementGroupPrototype(). W tym celu dodaj następujący kod do projektu Dsl:

```csharp

public class MyElementOperations : DesignSurfaceElementOperations
{
  // Create an EGP to add to the clipboard.
  // Called when the elements to be copied have been
  // collected into an ElementGroup.
 protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)
  {
 // Add the shapes and connectors:
 // Get the elements already in the group:
    ModelElement[] mels = elementGroup.ModelElements
        .Concat(elementGroup.ElementLinks) // Omit if the paste target is not the diagram.
        .ToArray();
 // Get their shapes:
    IEnumerable<PresentationElement> shapes =
       mels.SelectMany(mel =>
            PresentationViewsSubject.GetPresentation(mel));
    elementGroup.AddRange(shapes);

 return base.CreateElementGroupPrototype
           (elementGroup, elements, closureType);
  }

 public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)
      : base(serviceProvider, diagram)
  { }
}

// Replace the standard ElementOperations
// singleton with your own:
partial class MyDslDiagram // EDIT NAME
{
 /// <summary>
 /// Singleton ElementOperations attached to this diagram.
 /// </summary>
 public override DesignSurfaceElementOperations ElementOperations
  {
 get
    {
 if (singleton == null)
      {
        singleton = new MyElementOperations(this.Store as IServiceProvider, this);
      }
 return singleton;
    }
  }
 private MyElementOperations singleton = null;
}
```

 **Wklej kształty w wybranej lokalizacji, na przykład bieżące położenie kursora.**
Gdy użytkownik kopiuje wiele kształtów, można zachować ich położenie względne, gdy są wklejone. Tę technikę zademonstrował przykład w [vmsdk: circuit diagrams sample](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8).

 Aby osiągnąć ten efekt, zastąp metodę , aby użyć wersji specyficznej `ClipboardCommandSet.ProcessOnMenuPasteCommand()` dla lokalizacji programu `ElementOperations.Merge()` . W tym celu dodaj następujący kod w projekcie DslPackage:

```csharp

partial class MyDslClipboardCommandSet // EDIT NAME
{
   /// <summary>
    /// This method assumes we only want to paste things onto the diagram
    /// - not onto anything contained in the diagram.
    /// The base method pastes in a free space on the diagram.
    /// But if the menu was used to invoke paste, we want to paste in the cursor position.
    /// </summary>
    protected override void ProcessOnMenuPasteCommand()
    {

  NestedShapesSampleDocView docView = this.CurrentModelingDocView as NestedShapesSampleDocView;

      // Retrieve data from clipboard:
      System.Windows.Forms.IDataObject data = System.Windows.Forms.Clipboard.GetDataObject();

      Diagram diagram = docView.CurrentDiagram;
      if (diagram == null) return;

      if (!docView.IsContextMenuShowing)
      {
        // User hit CTRL+V - just use base method.

        // Deselect anything that's selected, otherwise
        // pasted item will be incompatible:
        if (!this.IsDiagramSelected())
        {
          docView.SelectObjects(1, new object[] { diagram }, 0);
        }

        // Paste into a convenient spare space on diagram:
    base.ProcessOnMenuPasteCommand();
      }
      else
      {
        // User right-clicked - paste at mouse position.

        // Utility class:
        DesignSurfaceElementOperations op = diagram.ElementOperations;

        ShapeElement pasteTarget = diagram;

        // Check whether what's in the paste buffer is acceptable on the target.
        if (pasteTarget != null && op.CanMerge(pasteTarget, data))
        {

        // Although op.Merge would be a no-op if CanMerge failed, we check CanMerge first
          // so that we don't create an empty transaction (after which Undo would be no-op).
          using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("paste"))
          {
            PointD place = docView.ContextMenuMousePosition;
            op.Merge(pasteTarget, data, PointD.ToPointF(place));
            t.Commit();
          }
        }
      }
    }
  }
```

 **Umożliwia użytkownikowi przeciąganie i upuszczanie elementów.**
Zobacz [How to: Add a Drag-and-Drop Handler (Jak dodać program obsługi przeciągania i upuszczania).](../modeling/how-to-add-a-drag-and-drop-handler.md)

## <a name="customizing-link-copy-behavior"></a><a name="customizeLinks"></a> Dostosowywanie zachowania kopiowania linków
 Gdy użytkownik kopiuje element, standardowym zachowaniem jest to, że kopiowane są również wszystkie osadzone elementy. Możesz zmodyfikować standardowe zachowanie podczas kopiowania. W definicji DSL wybierz rolę po jednej stronie relacji i w okno Właściwości ustaw **wartość Propagacja kopii.**

 ![Propaguje właściwość Copy roli domeny](../modeling/media/dslpropagatescopy.png)

 Istnieją trzy wartości:

- Nie propaguj kopii

- Propagacja kopii tylko do linku — gdy grupa zostanie wklejona, nowa kopia tego linku będzie odwoływać się do istniejącego elementu na drugim końcu linku.

- Propagacja kopii do linku i przeciwległego odtwarzacza roli — skopiowana grupa zawiera kopię elementu na drugim końcu linku.

  ![Efekt kopiowania za pomocą propagateCopyToLinkOnly](../modeling/media/dslpropagatecopy.png)

  Wprowadzone zmiany będą mieć wpływ zarówno na elementy, jak i skopiowany obraz.

## <a name="programming-copy-and-paste-behavior"></a>Programowanie zachowania kopiowania i wklejania
 Wiele aspektów zachowania DSL w odniesieniu do kopiowania, wklejania, tworzenia i usuwania obiektów są zarządzane przez wystąpienie, które jest <xref:Microsoft.VisualStudio.Modeling.ElementOperations> powiązane z diagramem. Zachowanie DSL można zmodyfikować, wyprowadzając własną klasę z i przesłaniając <xref:Microsoft.VisualStudio.Modeling.ElementOperations> <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> właściwość klasy diagramu.

> [!TIP]
> Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [Navigating and Updating a Model in Program Code (Nawigowanie i aktualizowanie modelu w kodzie programu).](../modeling/navigating-and-updating-a-model-in-program-code.md)

 ![Diagram sekwencji dla operacji kopiowania](../modeling/media/dslcopyseqdiagram.png)

 ![Diagram sekwencji operacji wklejania](../modeling/media/dslpasteseqdiagram.png)

#### <a name="to-define-your-own-elementoperations"></a>Aby zdefiniować własne elementy ElementOperations

1. W nowym pliku w projekcie DSL utwórz klasę pochodzącą od klasy <xref:Microsoft.VisualStudio.Modeling.Diagrams.DesignSurfaceElementOperations> .

2. Dodaj definicję klasy częściowej dla klasy diagramu. Nazwę tej klasy można znaleźć w pliku **Dsl\GeneratedCode\Diagrams.cs.**

    W klasie diagramu zastąp element ,  <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> aby zwrócić wystąpienie podklasy ElementOperations. To samo wystąpienie powinno zostać zwrócone przy każdym wywołaniu.

   Dodaj ten kod w pliku kodu niestandardowego w projekcie DslPackage:

```csharp

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;

  public partial class MyDslDiagram
  {
    public override DesignSurfaceElementOperations ElementOperations
    {
      get
      {
        if (this.elementOperations == null)
        {
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);
        }
        return this.elementOperations;
      }
    }
    private MyElementOperations elementOperations = null;
  }

  public class MyElementOperations : DesignSurfaceElementOperations
  {
    public MyElementOperations(IServiceProvider serviceProvider, MyDslDiagram diagram)
      : base(serviceProvider, diagram)
    { }
    // Overridden methods follow
  }
```

## <a name="receiving-items-dragged-from-other-models"></a>Odbieranie elementów przeciąganych z innych modeli
 ElementOperations może również służyć do definiowania zachowania kopiowania, przenoszenia, usuwania i przeciągania i upuszczania. Jako pokaz użycia elementu ElementOperations w przykładzie tutaj zdefiniowano niestandardowe zachowanie przeciągania i upuszczania. Jednak w tym celu można rozważyć alternatywne podejście opisane w te [tematze How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md)(Jak dodać program obsługi przeciągania i upuszczania), które jest bardziej rozszerzalne.

 Zdefiniuj dwie metody w klasie ElementOperations:

- `CanMerge(ModelElement targetElement, System.Windows.Forms.IDataObject data)` określa, czy element źródłowy można przeciągać do kształtu docelowego, łącznika lub diagramu.

- `MergeElementGroupPrototype(ModelElement targetElement, ElementGroupPrototype sourcePrototype)` który łączy element źródłowy z elementem docelowym.

### <a name="canmerge"></a>CanMerge()
 `CanMerge()` Jest wywoływana w celu określenia opinii, które powinny być podane użytkownikowi, gdy mysz przesuwa się przez diagram. Parametry metody to element, na którym znajduje się wskaźnik myszy, oraz dane dotyczące źródła, z którego wykonano operację przeciągania. Użytkownik może przeciągać z dowolnego miejsca na ekranie. W związku z tym obiekt źródłowy może mieć wiele różnych typów i może być serializowany w różnych formatach. Jeśli źródłem jest model DSL lub UML, parametr danych jest serializacji <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> . Operacje przeciągania, kopiowania i przybornika używają elementu ElementGroupPrototypes do reprezentowania fragmentów modeli.

 Prototyp grupy elementów może zawierać dowolną liczbę elementów i linków. Typy elementów mogą być identyfikowane za pomocą ich identyfikatorów GUID. Identyfikator GUID ma kształt, który został przeciągnięty, a nie bazowy element modelu. W poniższym przykładzie `CanMerge()` zwraca wartość true, jeśli kształt klasy z diagramu UML zostanie przeciągnięty do tego diagramu.

```csharp
public override bool CanMerge(ModelElement targetShape, System.Windows.Forms.IDataObject data)
 {
  // Extract the element prototype from the data.
  ElementGroupPrototype prototype = ElementOperations.GetElementGroupPrototype(this.ServiceProvider, data);
  if (targetShape is MyTargetShape && prototype != null &&
        prototype.RootProtoElements.Any(rootElement =>
          rootElement.DomainClassId.ToString()
          ==  "3866d10c-cc4e-438b-b46f-bb24380e1678")) // Guid of UML Class shapes
          // or SourceClass.DomainClassId
        return true;
   return base.CanMerge(targetShape, data);
 }
```

## <a name="mergeelementgroupprototype"></a>MergeElementGroupPrototype()
 Ta metoda jest wywoływana, gdy użytkownik porzuca element na diagramie, kształcie lub łączniku. Należy scalić przeciąganą zawartość z elementem docelowym. W tym przykładzie kod określa, czy rozpoznaje kombinację typów docelowych i prototypowych; Jeśli tak, metoda konwertuje przeciągane elementy na prototyp elementów, które powinny zostać dodane do modelu. Metoda podstawowa jest wywoływana w celu wykonania scalania z przekonwertowanych lub niezwerytowanych elementów.

```csharp
public override void MergeElementGroupPrototype(ModelElement targetShape, ElementGroupPrototype sourcePrototype)
{
  ElementGroupPrototype prototypeToMerge = sourcePrototype;
  MyTargetShape pel = targetShape as MyTargetShape;
  if (pel != null)
  {
    prototypeToMerge = ConvertDraggedTypeToLocal(pel, sourcePrototype);
  }
  if (prototypeToMerge != null)
    base.MergeElementGroupPrototype(targetShape, prototypeToMerge);
}
```

 Ten przykład dotyczy elementów klasy UML przeciąganych z diagramu klasy UML. Dsl nie jest przeznaczony do przechowywania klas UML bezpośrednio, ale zamiast tego tworzymy element DSL dla każdej przeciąganych klas UML. Może to być przydatne, na przykład jeśli DSL jest diagram wystąpienia. Użytkownik może przeciągać klasy na diagram, aby tworzyć wystąpienia tych klas.

```csharp

private ElementGroupPrototype ConvertDraggedTypeToLocal (MyTargetShape snapshot, ElementGroupPrototype prototype)
{
  // Find the UML project:
  EnvDTE.DTE dte = snapshot.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
  foreach (EnvDTE.Project project in dte.Solution.Projects)
  {
    IModelingProject modelingProject = project as IModelingProject;
    if (modelingProject == null) continue; // not a modeling project
    IModelStore store = modelingProject.Store;
    if (store == null) continue;
    // Look for the shape that was dragged:
    foreach (IDiagram umlDiagram in store.Diagrams())
    {
      // Get modeling diagram that implements UML diagram:
      Diagram diagram = umlDiagram.GetObject<Diagram>();
      Guid elementId = prototype.SourceRootElementIds.FirstOrDefault();
      ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
      if (shape == null) continue;
      IClass classElement = shape.ModelElement as IClass;
      if (classElement == null) continue;

      // Create a prototype of elements in my DSL, based on the UML element:
      Instance instance = new Instance(snapshot.Store);
      instance.Type = classElement.Name;
      // Pack them into a prototype:
      ElementGroup group = new ElementGroup(instance);
      return group.CreatePrototype();
    }
  }
  return null;
}
```

## <a name="standard-copy-behavior"></a>Standardowe zachowanie kopiowania
 Kod w tej sekcji przedstawia metody, które można przesłonić w celu zmiany zachowania kopiowania. Aby ułatwić ci zobaczenie sposobu osiągnięcia własnych dostosowań, w tej sekcji przedstawiono kod, który zastępuje metody związane z kopiowaniem, ale nie zmienia standardowego zachowania.

 Gdy użytkownik naciśnie klawisze CTRL +C lub użyje polecenia menu Kopiuj, wywoływana <xref:Microsoft.VisualStudio.Modeling.Shell.ClipboardCommandSet.ProcessOnMenuCopyCommand%2A> jest metoda . Możesz zobaczyć, jak to jest ustawione w **DslPackage\Generated Code\CommandSet.cs**. Aby uzyskać więcej informacji na temat sposobu skonfigurowania poleceń, zobacz Jak dodać polecenie do [menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 Możesz zastąpić metodę ProcessOnMenuCopyCommand, dodając częściową definicję klasy *MyDsl* `ClipboardCommandSet` w projekcie DslPackage.

```csharp
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

partial class MyDslClipboardCommandSet
{
  /// <summary>
  /// Override ProcessOnMenuCopyCommand() to copy elements to the
  /// clipboard in different formats, or to perform additional tasks
  /// before or after copying - for example deselect the copied elements.
  /// </summary>
  protected override void ProcessOnMenuCopyCommand()
  {
    IList<ModelElement> selectedModelElements = this.SelectedElements;
    if (selectedModelElements.Count == 0) return;

    // System container for clipboard data.
    // The IDataObject can contain data in several formats.
    IDataObject dataObject = new DataObject();

    Bitmap bitmap = null; // For export to other programs.
    try
    {
      #region Create EGP for copying to a DSL.
      this.CopyModelElementsIntoElementGroupPrototype
                     (dataObject, selectedModelElements);
      #endregion

      #region Create bitmap for copying to another application.
      // Find all the shapes associated with this selection:
      List<ShapeElement> shapes = new List<ShapeElement>(
        this.ResolveExportedShapesForClipboardImages
              (dataObject, selectedModelElements));

      bitmap = this.CreateBitmapForClipboard(shapes);
      if (bitmap != null)
      {
        dataObject.SetData(DataFormats.Bitmap, bitmap);
      }
      #endregion

      // Add the data to the clipboard:
      Clipboard.SetDataObject(dataObject, true, 5, 100);
    }
    finally
    {
      // Dispose bitmap after SetDataObject:
      if (bitmap != null) bitmap.Dispose();
    }
  }
/// <summary>
/// Override this to customize the element group that is copied to the clipboard.
/// </summary>
protected override void CopyModelElementsIntoElementGroupPrototype(IDataObject dataObject, IList<ModelElement> selectedModelElements)
{
  return this.ElementOperations.Copy(dataObject, selectedModelElements);
}
}
```

 Każdy diagram ma pojedyncze wystąpienie elementu ElementOperations. Możesz podać własne pochodne. Ten plik, który można umieścić w projekcie DSL, będzie zachowywać się tak samo jak kod, który zastępuje:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace Company.MyDsl
{
  partial class MyDslDiagram
  {
    /// <summary>
    /// Singleton ElementOperations attached to this diagram.
    /// </summary>
    public override DesignSurfaceElementOperations ElementOperations
    {
      get
      {
        if (this.elementOperations == null)
        {
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);
        }
        return this.elementOperations;
      }
    }
    private MyElementOperations elementOperations = null;
  }

  // Our own version of ElementOperations so that we can override:
  public class MyElementOperations : DesignSurfaceElementOperations
  {
    public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)
      : base(serviceProvider, diagram)
    { }

    /// <summary>
    /// Copy elements to the clipboard data.
    /// Provides a hook for adding custom data.
    /// </summary>
    public override void Copy(System.Windows.Forms.IDataObject data,
      ICollection<ModelElement> elements,
      ClosureType closureType,
      System.Drawing.PointF sourcePosition)
    {
      if (CanAddElementGroupFormat(elements, closureType))
      {
        AddElementGroupFormat(data, elements, closureType);
      }

      // Override these to store additional data:
      if (CanAddCustomFormat(elements, closureType))
      {
        AddCustomFormat(data, elements, closureType, sourcePosition);
      }
    }

    protected override void AddElementGroupFormat(System.Windows.Forms.IDataObject data, ICollection<ModelElement> elements, ClosureType closureType)
    {
      // Add the selected elements and those implied by the propagate copy rules:
      ElementGroup elementGroup = this.CreateElementGroup(elements, closureType);

      // Mark all the elements that are not embedded under other elements:
      this.MarkRootElements(elementGroup, elements, closureType);

      // Store in the clipboard data:
      ElementGroupPrototype elementGroupPrototype = this.CreateElementGroupPrototype(elementGroup, elements, closureType);
      data.SetData(ElementGroupPrototype.DefaultDataFormatName, elementGroupPrototype);
    }

    /// <summary>
    /// Override this to store additional elements in the element group:
    /// </summary>
    protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)
    {
      ElementGroupPrototype prototype = new ElementGroupPrototype(this.Partition, elementGroup.RootElements, elementGroup);
      return prototype;
    }

    /// <summary>
    /// Create an element group from the given starting elements, using the
    /// copy propagation rules specified in the DSL Definition.
    /// By default, this includes all the embedded descendants of the starting elements,
    /// and also includes reference links where both ends are already included.
    /// </summary>
    /// <param name="startElements">model elements to copy</param>
    /// <param name="closureType"></param>
    /// <returns></returns>
    protected override ElementGroup CreateElementGroup(ICollection<ModelElement> startElements, ClosureType closureType)
    {
      // ElementClosureWalker finds all the connected elements,
      // according to the propagate copy rules specified in the DSL Definition:
      ElementClosureWalker walker = new ElementClosureWalker(this.Partition,
        closureType, // Normally ClosureType.CopyClosure
        startElements,
        true, // Do not load other models.
        null, // Optional list of domain roles not to traverse.
        true); // Include relationship links where both ends are already included.

      walker.Traverse(startElements);
      IList<ModelElement> closureList = walker.ClosureList;
      Dictionary<object, object> closureContext = walker.Context;

      // create a group for this closure
      ElementGroup group = new ElementGroup(this.Partition);
      group.AddRange(closureList, false);

      // create the element group prototype for the group
      foreach (object key in closureContext.Keys)
      {
        group.SourceContext.ContextInfo[key] = closureContext[key];
      }

      return group;
    }
  }
}
```

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Przykład: przykład diagramów obwodu VMSDK](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
