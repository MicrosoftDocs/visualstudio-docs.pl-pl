---
title: Dostosowywanie zachowania dotyczącego kopiowania
description: Dowiedz się, że w DSL utworzonych za pomocą wizualizacji programu Visual Studio i zestawu SDK modelowania można zmienić to, co się dzieje, gdy użytkownik kopiuje i wklei elementy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8eee81440c0dda7f193d3e37eab700ada3ff259f
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363110"
---
# <a name="customizing-copy-behavior"></a>Dostosowywanie zachowania dotyczącego kopiowania
W języku specyficznym dla domeny (DSL) utworzonym za pomocą wizualizacji programu Visual Studio i zestawu SDK modelowania można zmienić to, co się dzieje, gdy użytkownik kopiuje i wklei elementy.

## <a name="standard-copy-and-paste-behavior"></a>Standardowe zachowanie kopiowania i wklejania
 Aby włączyć kopiowanie, ustaw właściwość **Włącz kopiowanie wklejenia** węzła **Edytor** w Eksploratorze DSL.

 Domyślnie, gdy użytkownik Kopiuje elementy do schowka, kopiowane są również następujące elementy:

- Osadzone elementy podrzędne wybranych elementów. (Czyli elementy, które są obiektami docelowymi relacji osadzania, które są źródłem w skopiowanych elementach).

- Linki relacji między skopiowanymi elementami.

  Ta reguła jest stosowana cyklicznie do skopiowanych elementów i linków.

  ![Skopiowane i wklejone elementy](../modeling/media/dslcopypastedefault.png)

  Skopiowane elementy i linki są serializowane i przechowywane w <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), które są umieszczane w Schowku.

  Obraz skopiowanych elementów jest również umieszczany w Schowku. Dzięki temu użytkownik może wklejać do innych aplikacji, takich jak Word.

  Użytkownik może wkleić skopiowane elementy do obiektu docelowego, który może akceptować elementy zgodnie z definicją DSL. Na przykład w przypadku linii DSL wygenerowanej na podstawie szablonu rozwiązania składniki użytkownik może wkleić porty do składników, ale nie do diagramu; i można wkleić składniki do diagramu, ale nie do innych składników.

## <a name="customizing-copy-and-paste-behavior"></a>Dostosowywanie zachowania kopiowania i wklejania
 Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 **Włącza lub wyłącza funkcję kopiowania, wycinania i wklejania.**
W Eksploratorze DSL ustaw właściwość **enable Copy Past** węzła **edytora** .

 **Kopiuj linki do tego samego obiektu docelowego.** Na przykład, aby skopiować pole komentarza połączonego z tym samym elementem podmiotu.
Ustaw właściwość **propagowania kopii** roli do **propagowania kopii tylko do konsolidacji**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopiowania linków](#customizeLinks).

 Kopiuj połączone elementy. Na przykład podczas kopiowania nowego elementu tworzone są również kopie wszystkich połączonych pól komentarzy.
Ustaw właściwość **propagowania kopii** roli w celu **propagowania kopii do konsolidacji i przeciwległego obiektu pełniącego rolę**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopiowania linków](#customizeLinks).

 **Szybkie duplikowanie elementów przez kopiowanie i wklejanie.** Normalnie skopiowany element jest nadal zaznaczony i nie można wkleić tego samego typu elementu.
Dodaj dyrektywę scalenia elementów do klasy domeny i ustaw ją na przekazanie do niej scalenia z klasą nadrzędną. Będzie to miało ten sam wpływ na operacje przeciągania. Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przenoszenia elementów](../modeling/customizing-element-creation-and-movement.md).

 \- oraz

 Przed wklejeniem elementów wybierz diagram, zastępując go `ClipboardCommandSet.ProcessOnPasteCommand()` . Dodaj ten kod do pliku niestandardowego w projekcie DslPackage:

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

 **Utwórz dodatkowe linki, gdy użytkownik wklei się w wybranym miejscu docelowym.** Na przykład po wklejeniu pola komentarza do elementu zostanie nawiązane połączenie między nimi.
Dodaj dyrektywę scalenia elementów do klasy domena docelowa i ustaw ją, aby przetworzyć Scalanie przez dodanie linków. Będzie to miało ten sam wpływ na operacje przeciągania. Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przenoszenia elementów](../modeling/customizing-element-creation-and-movement.md).

 \- oraz

 Przesłoń, `ClipboardCommandSet.ProcessOnPasteCommand()` Aby utworzyć dodatkowe linki po wywołaniu metody podstawowej.

 **Dostosuj formaty, w których elementy mogą być kopiowane** do aplikacji zewnętrznych — na przykład, aby dodać obramowanie do formularza mapy bitowej.
Zastąp *MyDsl* `ClipboardCommandSet.ProcessOnMenuCopyCommand()` w projekcie DslPackage.

 **Dostosuj sposób kopiowania elementów do schowka przez polecenie copy, ale nie w operacji przeciągania.**
Zastąp *MyDsl* `ClipboardCommandSet.CopyModelElementsIntoElementGroupPrototype()` w projekcie DslPackage.

 **Zachowaj układ kształtu przez kopiowanie i wklejanie.**
Gdy użytkownik kopiuje wiele kształtów, można zachować ich względne położenie podczas wklejania. Ta technika jest przedstawiona przez przykład na [VMSDK: diagramy obwodów](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8).

 Aby osiągnąć ten efekt, Dodaj kształty i łączniki do skopiowanego ElementGroupPrototype. Najbardziej wygodną metodą przesłonięcia jest ElementOperations. CreateElementGroupPrototype (). Aby to zrobić, Dodaj następujący kod do projektu DSL:

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

 **Wklej kształty w wybranej lokalizacji, na przykład w bieżącym położeniu kursora.**
Gdy użytkownik kopiuje wiele kształtów, można zachować ich względne położenie podczas wklejania. Ta technika jest przedstawiona przez przykład na [VMSDK: diagramy obwodów](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8).

 Aby osiągnąć ten efekt, Przesłoń, `ClipboardCommandSet.ProcessOnMenuPasteCommand()` Aby użyć wersji programu `ElementOperations.Merge()` . Aby to zrobić, Dodaj następujący kod w projekcie DslPackage:

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

 **Zezwól użytkownikowi na przeciąganie i upuszczanie elementów.**
Zobacz [jak: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="customizing-link-copy-behavior"></a><a name="customizeLinks"></a> Dostosowywanie zachowania kopiowania linków
 Gdy użytkownik kopiuje element, standardowe zachowanie polega na tym, że wszystkie osadzone elementy są również kopiowane. Można zmodyfikować zachowanie kopiowania standardowego. W definicji DSL wybierz rolę z jednej strony relacji i w okno Właściwości ustaw wartość **propagowanie kopii** .

 ![Propaguje Właściwość Copy roli domeny](../modeling/media/dslpropagatescopy.png)

 Istnieją trzy wartości:

- Nie propagowanie kopii

- Propaguj kopię do linku — w przypadku wklejenia grupy nowa kopia tego łącza odwołuje się do istniejącego elementu na drugim końcu łącza.

- Propagowanie kopii do linku i przeciwległego obiektu pełniącego rolę — skopiowana grupa zawiera kopię elementu na drugim końcu łącza.

  ![Efekt kopiowania z PropagateCopyToLinkOnly](../modeling/media/dslpropagatecopy.png)

  Wprowadzone zmiany wpłyną zarówno na elementy, jak i obraz, który jest kopiowany.

## <a name="programming-copy-and-paste-behavior"></a>Programowanie zachowań kopiowania i wklejania
 Wiele aspektów zachowania DSL w odniesieniu do kopiowania, wklejania, tworzenia i usuwania obiektów podlega wystąpieniu <xref:Microsoft.VisualStudio.Modeling.ElementOperations> , które jest powiązane z diagramem. Możesz zmodyfikować zachowanie DSL, wprowadzając własną klasę z <xref:Microsoft.VisualStudio.Modeling.ElementOperations> i zastępując <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> Właściwość klasy diagramu.

> [!TIP]
> Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 ![Diagram sekwencji operacji kopiowania](../modeling/media/dslcopyseqdiagram.png)

 ![Diagram sekwencji operacji wklejania](../modeling/media/dslpasteseqdiagram.png)

#### <a name="to-define-your-own-elementoperations"></a>Aby zdefiniować własne ElementOperations

1. W nowym pliku w projekcie DSL Utwórz klasę, która pochodzi od <xref:Microsoft.VisualStudio.Modeling.Diagrams.DesignSurfaceElementOperations> .

2. Dodaj definicję klasy częściowej dla klasy diagramu. Nazwę tej klasy można znaleźć w **Dsl\GeneratedCode\Diagrams.cs**.

    W klasie diagram Przesłoń,  <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> Aby zwrócić wystąpienie podklasy ElementOperations. Należy zwrócić to samo wystąpienie przy każdym wywołaniu.

   Dodaj ten kod w pliku niestandardowego kodu w projekcie DslPackage:

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

## <a name="receiving-items-dragged-from-other-models"></a>Pobieranie elementów przeciąganych z innych modeli
 ElementOperations można także użyć do zdefiniowania zachowania kopiowania, przenoszenia, usuwania i przeciągania i upuszczania. Przykładowo w przypadku korzystania z ElementOperations, podano w tym miejscu sposób definiowania niestandardowego zachowania przeciągania i upuszczania. Jednakże w tym celu można wziąć pod uwagę alternatywne podejście opisane w [instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md), co jest bardziej rozszerzalne.

 Zdefiniuj dwie metody w klasie ElementOperations:

- `CanMerge(ModelElement targetElement, System.Windows.Forms.IDataObject data)` Określa, czy element źródłowy może być przeciągany do kształtu docelowego, łącznika lub diagramu.

- `MergeElementGroupPrototype(ModelElement targetElement, ElementGroupPrototype sourcePrototype)` łączący element źródłowy z elementem docelowym.

### <a name="canmerge"></a>Anuluj scalanie ()
 `CanMerge()` jest wywoływana, aby określić opinię, która powinna zostać udzielona użytkownikowi, gdy wskaźnik myszy zostanie przesunięty na diagram. Parametry metody to element, nad którym wskaźnik myszy jest aktywowany, i dane dotyczące źródła, z którego wykonano operację przeciągania. Użytkownik może przeciągać z dowolnego miejsca na ekranie. W związku z tym obiekt źródłowy może być wielu różnych typów i może być serializowany w różnych formatach. Jeśli źródłem jest model DSL lub UML, parametr danych jest serializacji <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> . Operacje przeciągania, kopiowania i przybornika używają ElementGroupPrototypes do reprezentowania fragmentów modeli.

 Prototyp grupy elementów może zawierać dowolną liczbę elementów i linków. Typy elementów mogą być identyfikowane przez ich identyfikatory GUID. Identyfikator GUID jest kształtu, który został przeciągnięty, a nie do bazowego elementu modelu. W poniższym przykładzie `CanMerge()` zwraca wartość true, jeśli kształt klasy z DIAGRAMU UML jest przeciągany na ten diagram.

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
 Ta metoda jest wywoływana, gdy użytkownik porzuca element na diagramie, kształcie lub łączniku. Należy scalić przeciąganą zawartość do elementu docelowego. W tym przykładzie kod określa, czy rozpoznaje kombinację elementów docelowych i typów prototypów. Jeśli tak, Metoda konwertuje przeciągane elementy do prototypu elementów, które powinny zostać dodane do modelu. Metoda bazowa jest wywoływana, aby wykonać scalanie, w przypadku przekonwertowanych lub nieprzekonwertowanych elementów.

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

 Ten przykład dotyczy elementów klasy UML przeciąganych z diagramu klas UML. DSL nie jest przeznaczone do bezpośredniego przechowywania klas UML, ale zamiast tego tworzymy element DSL dla każdej przeciąganej klasy UML. Może to być przydatne, na przykład jeśli DSL jest diagramem wystąpienia. Użytkownik może przeciągać klasy na diagram, aby utworzyć wystąpienia tych klas.

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
 Kod w tej sekcji zawiera metody, które można przesłonić, aby zmienić zachowanie kopiowania. Aby ułatwić dowiedzieć się, jak osiągnąć własne dostosowania, w tej sekcji przedstawiono kod, który zastępuje metody związane z kopiowaniem, ale nie zmienia zachowania standardowego.

 Gdy użytkownik naciśnie kombinację klawiszy CTRL + C lub używa polecenia Kopiuj menu, Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.ClipboardCommandSet.ProcessOnMenuCopyCommand%2A> jest wywoływana. Możesz zobaczyć, jak to jest skonfigurowane w **DslPackage\Generated Code\CommandSet.cs**. Aby uzyskać więcej informacji o konfigurowaniu poleceń, zobacz [jak: Dodawanie polecenia do menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 Możesz przesłonić ProcessOnMenuCopyCommand, dodając częściową definicję klasy *MyDsl* `ClipboardCommandSet` w projekcie DslPackage.

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

 Każdy diagram ma pojedyncze wystąpienie ElementOperations. Możesz podać własne pochodne. Ten plik, który może być umieszczony w projekcie DSL, zachowuje się tak samo jak kod, który zastąpi:

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
- [Przykład: Przykładowe diagramy obwodów VMSDK](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
