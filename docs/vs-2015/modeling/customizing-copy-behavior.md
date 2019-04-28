---
title: Dostosowywanie zachowania dotyczącego kopiowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 87fff01c-60ba-440a-b8a0-185edcef83ac
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b88d3541bc9c3b2f890c2aadf0103c48d3dad865
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433301"
---
# <a name="customizing-copy-behavior"></a>Dostosowywanie zachowania dotyczącego kopiowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W języku specyficznym dla domeny (DSL) utworzone za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wizualizacji i modelowania SDK można zmienić, co się dzieje, gdy użytkownik kopiuje i wkleja elementów.  
  
## <a name="standard-copy-and-paste-behavior"></a>Standardowa kopiowania i wklejania zachowanie  
 Aby włączyć, kopiowanie, ustaw **Włącz kopiowanie wklejanie** właściwość **edytora** węzła w Eksploratorze DSL.  
  
 Domyślnie gdy użytkownik kopiuje elementy do Schowka, następujące elementy są również kopiowane:  
  
- Osadzone elementy podrzędne elementu wybranych elementów. (Oznacza to, elementy, które są cele osadzania relacje, które rozwijani w modelu są kopiowane elementy).  
  
- Łączy relacji między skopiowane elementy.  
  
  Ta reguła ma charakter cykliczny skopiowane elementy i łącza.  
  
  ![Skopiować i wkleić elementy](../modeling/media/dslcopypastedefault.png "DslCopyPasteDefault")  
  
  Skopiowane elementy i łącza są serializowane i przechowywane w <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), który znajduje się w Schowku.  
  
  Obraz przedstawiający skopiowane elementy jest również umieszczona w Schowku. Dzięki temu użytkownikowi skopiować do innych aplikacji, takich jak Word.  
  
  Użytkownik może Wklej skopiowane elementy do obiektu docelowego, który może akceptować elementy według definicji DSL. Na przykład DSL generowany na podstawie szablonu rozwiązania składniki, użytkownik może Wklej w porty na składniki, ale nie na diagram; i wkleić składników na diagram, ale nie do innych składników.  
  
## <a name="customizing-copy-and-paste-behavior"></a>Dostosowywanie kopiowania i wklejania zachowania  
 Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 **Włącz lub wyłącz kopiowania, wycinania i wklejania.**  
 W Eksploratorze DSL, ustaw **Włącz kopiowanie wklejanie** właściwość **edytora** węzła.  
  
 **Skopiuj łącza do tej samej wartości docelowej.** Na przykład aby pole komentarza skopiowany połączony z tego samego elementu podmiotu.  
 Ustaw **propaguje kopiowania** właściwości roli **Propagacja kopiowania, aby połączyć tylko**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie łącze zachowania dotyczącego kopiowania](#customizeLinks).  
  
 Skopiuj połączone elementy. Na przykład podczas kopiowania nowego elementu kopie dowolnych polach komentarz połączony są wprowadzane również.  
 Ustaw **propaguje kopiowania** właściwości roli **Propagacja kopiowania do łącza, a obiekt pełniący rolę odwrotną**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie łącze zachowania dotyczącego kopiowania](#customizeLinks).  
  
 **Szybko zduplikowane elementy przez kopiowanie i wklejanie.** Zwykle element, który właśnie został skopiowany nadal zaznaczone i nie można wkleić ten sam typ elementu na niego.  
 Dodaj dyrektywa scalania elementów do klasy domeny i ustaw ją do scalenia do przodu do klasy nadrzędnej. Będzie to mieć ten sam efekt w operacji przeciągania. Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md).  
  
 \- lub —  
  
 Wybierz diagram przed wklejeniem elementów, poprzez zastąpienie `ClipboardCommandSet.ProcessOnPasteCommand()`. Dodaj następujący kod w pliku użytkownika projektu DslPackage:  
  
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
  
 **Utwórz dodatkowe linki, gdy użytkownik Wkleja do wybranego obiektu docelowego.** Na przykład gdy pole komentarza jest wklejany na element, powstaje łącze między nimi.  
 Dodaj dyrektywy scalenia elementów do klasy domeny docelowej i ustaw ją do przetwarzania scalania, dodając łącza. Będzie to mieć ten sam efekt w operacji przeciągania. Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md).  
  
 \- lub —  
  
 Zastąp `ClipboardCommandSet.ProcessOnPasteCommand()` utworzyć linki do dodatkowych po wywołaniu metody podstawowej.  
  
 **Dostosowywanie formaty, w których mogą być kopiowane elementy** do aplikacji zewnętrznych — na przykład, aby dodać obramowanie do formularza mapy bitowej.  
 Zastąp *MyDsl* `ClipboardCommandSet.ProcessOnMenuCopyCommand()` w projekcie DslPackage.  
  
 **Dostosowywanie, jak elementy są kopiowane do Schowka, za pomocą polecenia Kopiuj, ale nie w operacji przeciągania.**  
 Zastąp *MyDsl* `ClipboardCommandSet.CopyModelElementsIntoElementGroupPrototype()` w projekcie DslPackage.  
  
 **Zachowaj układ kształtu przy użyciu kopii i Wklej.**  
 Po użytkownik kopiuje wielu kształtów, można zachować swoje położenie względne, gdy zostaną wklejone. Ta technika jest przedstawiona według przykładu w [VMSDK: Przykładowe diagramy obwodu](http://go.microsoft.com/fwlink/?LinkId=213879).  
  
 Aby uzyskać ten efekt, Dodaj kształty i łączniki do ElementGroupPrototype skopiowany. Najbardziej wygodną metodę, aby zastąpić to ElementOperations.CreateElementGroupPrototype(). Aby to zrobić, Dodaj następujący kod do projektu Dsl:  
  
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
  
 **Wklejanie kształtów w wybranej lokalizacji, na przykład w bieżącej pozycji kursora.**  
 Po użytkownik kopiuje wielu kształtów, można zachować swoje położenie względne, gdy zostaną wklejone. Ta technika jest przedstawiona według przykładu w [VMSDK: Przykładowe diagramy obwodu](http://go.microsoft.com/fwlink/?LinkId=213879).  
  
 Aby uzyskać ten efekt, Zastąp `ClipboardCommandSet.ProcessOnMenuPasteCommand()` użyć lokalizacji określonej wersji `ElementOperations.Merge()`. Aby to zrobić, Dodaj następujący kod w projekcie DslPackage:  
  
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
  
 **Umożliwia użytkownikowi na przeciąganie i upuszczanie elementów.**  
 Zobacz [jak: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="customizeLinks"></a> Dostosowywanie zachowania dotyczącego kopiowania łącza  
 Po użytkownik kopiuje element, standardowe zachowanie jest dowolnym osadzone elementy są również kopiowane. Standardowe zachowanie kopiowania można modyfikować. W definicji DSL, wybierz rolę po jednej stronie relacji i w zestawie okna właściwości **propaguje kopiowania** wartość.  
  
 ![Propaguje właściwości kopiowania roli domeny](../modeling/media/dslpropagatescopy.png "DslPropagatesCopy")  
  
 Istnieją trzy wartości:  
  
- Propagowanie nie Kopiuj  
  
- Propagacja kopiowania, aby połączyć tylko - po wklejeniu grupy, nowa kopia tego łącza będzie odnosił się do istniejącego elementu na drugim końcu łącza.  
  
- Propagacja kopiowania, aby połączyć, a obiekt pełniący rolę - odwrotną skopiowany grupa zawiera kopię elementu na drugim końcu łącza.  
  
  ![Działania kopiowania przy użyciu PropagateCopyToLinkOnly](../modeling/media/dslpropagatecopy.png "DslPropagateCopy")  
  
  Zmiany, które wpłynie zarówno elementy, jak i obraz, który jest kopiowany.  
  
## <a name="programming-copy-and-paste-behavior"></a>Kopiuj programowania i zachowanie wklejania  
 Wiele aspektów zachowania DSL w odniesieniu do kopiowania, wklejania, tworzenia i usuwania obiektów są regulowane przez wystąpienie <xref:Microsoft.VisualStudio.Modeling.ElementOperations> , jest sprzężona do diagramu. Można zmodyfikować zachowanie DSL wyprowadzanie klasy z <xref:Microsoft.VisualStudio.Modeling.ElementOperations> i zastępowanie <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> właściwości diagramu klasy.  
  
> [!TIP]
> Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 ![Diagram sekwencji operacji kopiowania](../modeling/media/dslcopyseqdiagram.png "dslCopySeqDiagram")  
  
 ![Diagram sekwencji operacji wklejania](../modeling/media/dslpasteseqdiagram.png "dslPasteSeqDiagram")  
  
#### <a name="to-define-your-own-elementoperations"></a>Aby zdefiniować własne ElementOperations  
  
1. W nowym pliku w projekcie języka DSL, należy utworzyć klasę, która jest pochodną <xref:Microsoft.VisualStudio.Modeling.Diagrams.DesignSurfaceElementOperations>.  
  
2. Dodaj definicję klasy częściowej klasy diagramu. Nazwa tej klasy można znaleźć w **Dsl\GeneratedCode\Diagrams.cs**.  
  
    W klasie diagram zastąpić <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> do zwrócenia wystąpienia usługi podklasy ElementOperations. To samo wystąpienie w każdym wywołaniu powinna zostać zwrócona.  
  
   Dodaj następujący kod w pliku niestandardowego kodu w projekcie DslPackage:  
  
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
  
## <a name="receiving-items-dragged-from-other-models"></a>Odbieranie elementów przeciągnięte z innymi modelami  
 ElementOperations może również służyć do definiowania zachowania kopiowania, przenoszenie, usuwanie i przeciągania i upuszczania. Jako pokaz użytkowania ElementOperations przykład podane tutaj definiuje niestandardowe zachowanie przeciągnij i upuść. Jednak w tym celu należy rozważyć alternatywne podejście, które opisano w [jak: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md), co jest bardziej rozszerzonego.  
  
 Zdefiniuj dwie metody w klasie ElementOperations:  
  
- `CanMerge(ModelElement targetElement, System.Windows.Forms.IDataObject data)` który określa, czy element źródła można przeciągać docelowej kształtu, łącznika lub diagramu.  
  
- `MergeElementGroupPrototype(ModelElement targetElement, ElementGroupPrototype sourcePrototype)` które łączy elementu źródłowego do docelowego.  
  
### <a name="canmerge"></a>CanMerge()  
 `CanMerge()` jest wywoływana, aby określić opinie, które należy nadać użytkownikowi, jako wskaźnik myszy porusza się na diagramie. Parametry metody są elementu, nad którym znajduje się kursor i dane dotyczące źródła, z którego została wykonana operacja przeciągania. Użytkownik można przeciągnąć z dowolnego miejsca na ekranie. W związku z obiektem źródłowym może mieć wiele różnych typów i może być serializowany w różnych formatach. Jeśli źródło jest modelu DSL lub UML, parametr danych jest serializacji <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Operacje przeciągania, kopiowanie i przybornika używają ElementGroupPrototypes do reprezentowania fragmenty modeli.  
  
 Prototyp grupy Element może zawierać dowolną liczbę elementów i łącza. Typy elementów można zidentyfikować według ich identyfikatorów. Identyfikator GUID jest kształtu, który został przeciągnięty nie bazowego elementu modelu. W poniższym przykładzie `CanMerge()` zwraca wartość true, jeśli klasa kształtu z diagramu UML jest przeciągany na tym diagramie.  
  
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
 Ta metoda jest wywoływana, gdy użytkownik porzuca element na diagram, kształtu lub łącznika. Należy go scalić przeciąganego zawartość elementu docelowego. W tym przykładzie kodu Określa, czy rozpoznaje kombinacji typów obiektu docelowego i prototypu. Jeśli tak, Metoda ta konwertuje przeciągane elementy do prototypu elementów, które powinny zostać dodane do modelu. Metoda podstawowa jest wywoływana, aby wykonać scalanie, albo przekonwertowanego lub nieprzekonwertowane elementów.  
  
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
  
 Ten przykład dotyczy elementów klasy UML przeciągnięte z diagramu klas UML. Język DSL nie jest przeznaczony do przechowywania klas UML bezpośrednio, ale zamiast tego, możemy utworzyć element DSL dla każdej przeciąganego klasy UML. Spowoduje to być przydatne, na przykład, jeśli język DSL jest diagram wystąpienia. Użytkownik można przeciągnąć klasy na niego przeciągnięte do tworzenia wystąpień tych klas.  
  
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
  
## <a name="standard-copy-behavior"></a>Zachowania dotyczącego kopiowania standardowe  
 Kod w tej sekcji przedstawiono metody, które można przesłonić, aby zmienić zachowanie kopiowania. Aby ułatwić Zobacz, jak utworzyć własne dostosowania osiągnąć w tej sekcji przedstawiono kod, który zastępuje metody związane z kopiowania, ale nie zmienia standardowe zachowanie.  
  
 Gdy użytkownik naciśnie klawisze CTRL + C lub korzysta z polecenia menu kopia, Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.ClipboardCommandSet.ProcessOnMenuCopyCommand%2A> jest wywoływana. Zobaczysz, jak to jest skonfigurowana w **DslPackage\Generated Code\CommandSet.cs**. Aby uzyskać więcej informacji na temat sposobu polecenia są konfigurowanie Zobacz [jak: Dodawanie polecenia do Menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
 Możesz zastąpić ProcessOnMenuCopyCommand przez dodanie definicji klasy częściowej *MyDsl* `ClipboardCommandSet` w projekcie DslPackage.  
  
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
  /// before or after copying – for example deselect the copied elements.  
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
  
 Każdy diagram ma pojedyncze wystąpienie ElementOperations. Możesz podać własne utworów zależnych. Ten plik, który można umieścić w projekcie języka DSL, będzie się zachowywał tak taki sam jak kod, który zastępuje ona:  
  
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
 [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md)   
 [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Dostosowywanie zachowania dotyczącego usuwania](../modeling/customizing-deletion-behavior.md)   
 [Przykład: Przykładowe wykresy obwodu VMSDK](http://go.microsoft.com/fwlink/?LinkId=213879)
