---
title: Wyświetlanie modelu UML na diagramach | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2c68089615fd38276e428df6ffaa906d0b3f6742
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770665"
---
# <a name="display-a-uml-model-on-diagrams"></a>Wyświetlanie modelu UML na diagramach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W kodzie programu do rozszerzenia programu Visual Studio można kontrolować sposób wyświetlania elementów modelu na diagramach. Aby dowiedzieć się, które wersje programu Visual Studio obsługują modeli UML, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 W tym temacie:  
 -   [Do wyświetlania elementu na diagramie](#Display)  
  
-   [Uzyskiwanie dostępu do kształtów, reprezentujących element](#GetShapes)  
  
-   [Przenoszenie i zmienianie rozmiaru kształtów](#Moving)  
  
-   [Aby usunąć kształtu z diagramu](#Removing)  
  
-   [Otwierania i tworzenia diagramów](#Opening)  
  
-   [Przykład: Polecenia wyrównywania kształtów](#AlignCommand)  
  
##  <a name="Display"></a> Do wyświetlania elementu na diagramie  
 Podczas tworzenia elementu, takiego jak przypadek użycia lub akcję, użytkownik może go wyświetlić w Eksploratorze modelu UML, ale nie zawsze są automatycznie wyświetlane na diagramie. W niektórych przypadkach należy napisać kod, aby go wyświetlić. Poniższa tabela zawiera podsumowanie alternatyw.  
  
|Typ elementu|Na przykład|Do wyświetlenia w tym, kod musi|  
|---------------------|-----------------|-------------------------------------|  
|Klasyfikator|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|Utworzenie skojarzone kształtów na diagramach określony. Można utworzyć dowolną liczbę kształty dla każdego klasyfikatora.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> Ustaw `parentShape` do `null` dla kształtu na najwyższym poziomie diagramu.<br /><br /> Aby wyświetlić jeden kształt wewnątrz innego:<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);` **Uwaga:**  Jeśli wykonujesz wyświetlania wewnątrz **ILinkedUndo** transakcji, metoda zwraca czasami nie `IShape`. Jednak kształt poprawnie jest tworzony i jest dostępne przy użyciu `IElement.Shapes().`|  
|Element podrzędny elementu klasyfikatora|Atrybutu, operacji<br /><br /> Części i portów|Automatyczne — kod nie jest wymagany.<br /><br /> Jest on wyświetlany jako część elementu nadrzędnego.|  
|Zachowanie|Interakcji (kolejny)<br /><br /> Działanie|Powiąż zachowanie odpowiednie diagramu.<br /><br /> Każde działanie może być powiązana z co najwyżej jeden diagram, w danym momencie.<br /><br /> Na przykład:<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|  
|Element podrzędny elementu zachowanie|Linie życia, wiadomości, akcje, węzłów obiektowych|Automatyczne — kod nie jest wymagany.<br /><br /> Jest on wyświetlany, jeśli element nadrzędny jest powiązany z diagramu.|  
|Relacja|Skojarzenie, Generalizacja, przepływ i zależności|Automatyczne — kod nie jest wymagany.<br /><br /> Jest on wyświetlany na każdy diagram, na którym są wyświetlane obu końcach.|  
  
##  <a name="GetShapes"></a> Uzyskiwanie dostępu do kształtów, reprezentujących element  
 Kształt, który reprezentuje element należy do typów:  
  
 `IShape`  
  
 `IShape<` *ElementType* `>`  
  
 gdzie *ElementType* jest typem elementu modelu, takie jak `IClass` lub `IUseCase`.  
  
|||  
|-|-|  
|`anElement.Shapes ()`|Wszystkie `IShapes` reprezentujące ten element na diagramach open.|  
|`anElement.Shapes(aDiagram)`|Wszystkie `IShapes` reprezentujące tego elementu na diagramie określonej.|  
|`anIShape.GetElement()`|`IElement` Który reprezentuje kształt. Będzie zazwyczaj rzutować do podklasy IElement.|  
|`anIShape.Diagram`|`IDiagram` Zawierający kształtu.|  
|`anIShape.ParentShape`|Kształt, który zawiera `anIShape`. Na przykład kształt portu znajduje się w obrębie kształtu składnika.|  
|`anIShape.ChildShapes`|Kształty zawartych w `IShape` lub `IDiagram`.|  
|`anIShape.GetChildShapes<IUseCase>()`|Kształty zawartych w `IShape` lub `IDiagram` reprezentujące elementy określonego typu, takie jak `IUseCase`.|  
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|Rzutowanie ogólnego `IShape` na silnie typizowaną `IShape<IElement>`.|  
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|Rzutowanie kształtu z typu jeden kształt parametryczne do innego.|  
  
##  <a name="Moving"></a> Przenoszenie i zmienianie rozmiaru kształtów  
  
|||  
|-|-|  
|`anIShape.Move(x, y, [width], [height])`|Przenoszenie lub zmienianie rozmiaru kształtu.|  
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|Uaktywnij okno, a następnie przewiń diagramu, tak że danego kształty są widoczne. Kształty musi być na diagramie. Jeśli `zoomToFit` ma wartość true, diagram skalowania w razie potrzeby, aby wszystkie kształty są widoczne.|  
  
 Aby uzyskać przykład, zobacz [Definiowanie polecenia wyrównanie](#AlignCommand).  
  
##  <a name="Removing"></a> Aby usunąć kształtu z diagramu  
 Możesz usunąć kształty niektóre typy elementu, bez usuwania elementu.  
  
|Element modelu|Aby usunąć kształt|  
|-------------------|-------------------------|  
|Klasyfikator: klasy, interfejsu, wyliczenia, aktora, przypadek użycia lub składnika|`shape.Delete();`|  
|Działanie: działanie i interakcji|Usuń z diagramu, z projektu. Użyj `IDiagram.FileName` uzyskać ścieżki.<br /><br /> To zachowanie nie powoduje usunięcia z modelu.|  
|Inne kształtu|Nie można jawnie usunąć inne kształty z diagramu. Kształt znikną automatycznie, czy element został usunięty z modelu, czy kształt nadrzędny zostanie usunięty z diagramu.|  
  
##  <a name="Opening"></a> Otwierania i tworzenia diagramów  
  
### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>Dostęp do bieżącego diagramu użytkownika z poziomu rozszerzenia poleceń lub gest  
 Zadeklaruj właściwość ta importowanych w klasie:  
  
 `[Import]`  
  
 `IDiagramContext Context { get; set; }`  
  
 W metodzie uzyskiwanie dostępu do diagramu:  
  
 `IClassDiagram classDiagram =`  
  
 `Context.CurrentDiagram as IClassDiagram;`  
  
> [!NOTE]
>  Wystąpienie `IDiagram` (i jego podtypów, takie jak `IClassDiagram`) jest prawidłowy tylko wewnątrz polecenia skuteczność przetwarzania. Nie zaleca się zachować `IDiagram` obiektu w zmiennej, która będzie nadal występować, gdy kontrolka jest zwracana do użytkownika.  
  
 Aby uzyskać więcej informacji, zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="to-obtain-a-list-of-open-diagrams"></a>Aby uzyskać listę otwieranie diagramów  
 Lista diagramy, które są aktualnie otwarte w projekcie:  
  
```  
Context.CurrentDiagram.ModelStore.Diagrams()  
```  
  
## <a name="to-access-the-diagrams-in-a-project"></a>Diagramy w projekcie dostęp do  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Interfejsu API może służyć do otwierania i tworzenia projektów i diagramów modelowania.  
  
 Zwróć uwagę, rzutowanie z `EnvDTE.ProjectItem` do `IDiagramContext`.  
  
```  
  
      using EnvDTE; // Visual Studio API  
...  
[Import]  
public IServiceProvider ServiceProvider { get; set; }  
...  
// Get Visual Studio API  
DTE dte = ServiceProvider.GetService(typeof(DTE)) as DTE;  
// Get current Visual Studio project  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
// Open and process every diagram in the project.  
foreach (ProjectItem item in project.ProjectItems)  
{  
  // Cast ProjectItem to IDiagramContext  
  IDiagramContext context = item as IDiagramContext;  
  if (context == null)  
  {  
     // This is not a diagram file.  
     continue;  
  }  
  // Open the file and give the window the focus.  
  if (!item.IsOpen)  
  {  
      item.Open().Activate();  
  }  
  // Get the diagram.  
  IDiagram diagram = context.CurrentDiagram;  
  // Deal with specific diagram types.  
  ISequenceDiagram seqDiagram = diagram as ISequenceDiagram;  
  if (seqDiagram != null)  
  { ... } } }  
```  
  
 Wystąpienia elementu `IDiagram` i jego podtypy nie są prawidłowe, po przywrócenie kontroli działowi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Możesz również uzyskać magazyn modeli z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu:  
  
```  
  
      Project project = ...;  
IModelStore modelStore = (project as IModelingProject).Store;  
```  
  
##  <a name="AlignCommand"></a> Przykład: Polecenia wyrównywania kształtów  
 Poniższy kod implementuje polecenie menu, pasującą starannego kształtów. Użytkownik wcześniej umieścić dwóch lub więcej kształtów w przybliżony wyrównanie poziomo lub pionowo. Następnie polecenia Wyrównaj może służyć do wyrównania ich centrów.  
  
 Aby udostępnić polecenie, Dodaj następujący kod, aby projekt polecenia menu, a następnie wdrożyć wynikowy rozszerzenia dla użytkowników. Aby uzyskać więcej informacji, zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace AlignCommand  
{  
  // Implements a command to align shapes in a UML class diagram.  
  // The user first selects shapes that are roughly aligned either vertically or horizontally.  
  // This command will straighten them up.  
  
  // Place this file in a menu command extension project.  
  // See http://msdn.microsoft.com/library/ee329481.aspx  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension] // TODO: Add other diagram types if needed  
  class CommandExtension : ICommandExtension  
  {  
    /// <summary>  
    /// See http://msdn.microsoft.com/library/ee329481.aspx  
    /// </summary>  
    [Import]  
    IDiagramContext context { get; set; }  
  
    /// <summary>  
    /// Transaction context.  
    /// See http://msdn.microsoft.com/library/ee330926.aspx  
    /// </summary>  
    [Import]  
    ILinkedUndoContext linkedUndo { get; set; }  
  
    /// <summary>  
    /// Called when the user selects the command.  
    /// </summary>  
    /// <param name="command"></param>  
    public void Execute(IMenuCommand command)  
    {  
      Align(context.CurrentDiagram.SelectedShapes);  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks on the diagram.  
    /// Determines whether the command is enabled.  
    /// </summary>  
    /// <param name="command"></param>  
    public void QueryStatus(IMenuCommand command)  
    {  
      IEnumerable<IShape> currentSelection = context.CurrentDiagram.SelectedShapes;  
      // Make it visible if there are shapes selected:  
      command.Visible = currentSelection.Count() > 0 && !(currentSelection.FirstOrDefault() is IDiagram);  
  
      // Make it enabled if there are two or more shapes that are roughly in line:  
      command.Enabled = currentSelection.Count() > 1  
        && (HorizontalAlignCenter(currentSelection) > 0.0  
        || VerticalAlignCenter(currentSelection) > 0.0);  
  
    }  
  
    /// <summary>  
    /// Title of the menu command.  
    /// </summary>  
    public string Text  
    {  
      get { return "Align Shapes"; }  
    }  
  
    /// <summary>  
    /// Find a horizontal line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double HorizontalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double Y = -1.0;  
      double top = 0.0, bottom = shapes.First().Bottom();  
      foreach (IShape shape in shapes)  
      {  
        top = Math.Max(top, shape.Top());  
        bottom = Math.Min(bottom, shape.Bottom());  
      }  
      if (bottom > top) Y = (bottom + top) / 2.0;  
      return Y;  
    }  
  
    /// <summary>  
    /// Find a vertical line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double VerticalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double X = -1.0;  
      double left = 0.0, right = shapes.First().Right();  
      foreach (IShape shape in shapes)  
      {  
        left = Math.Max(left, shape.Left());  
        right = Math.Min(right, shape.Right());  
      }  
      if (right > left) X = (right + left) / 2.0;  
      return X;  
    }  
  
    /// <summary>  
    /// Line up those shapes that are roughly aligned.  
    /// </summary>  
    /// <param name="shapes"></param>  
    private void Align(IEnumerable<IShape> shapes)  
    {  
      if (shapes.Count() > 1)  
      {  
        // The shapes must all overlap either horizontally or vertically.  
        // Find a horizontal line that is covered by all the shapes:  
        double Y = HorizontalAlignCenter(shapes);  
        if (Y > 0.0) // Negative if they don't overlap.  
        {  
          // Adjust all the shape positions in one transaction:  
          using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
          {  
            foreach (IShape shape in shapes)  
            {  
              shape.AlignYCenter(Y);  
            }  
            t.Commit();  
          }  
        }  
        else  
        {  
          // Find a vertical line that is covered by all the shapes:  
          double X = VerticalAlignCenter(shapes);  
          if (X > 0.0) // Negative if they don't overlap.  
          {  
            // Adjust all the shape positions in one transaction:  
            using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
            {  
              foreach (IShape shape in shapes)  
              {  
                shape.AlignXCenter(X);  
              }  
              t.Commit();  
            }  
          }  
        }  
      }  
    }  
  }  
  
  /// <summary>  
  /// Convenience extensions for IShape.  
  /// </summary>  
  public static class IShapeExtension  
  {  
    public static double Bottom(this IShape shape)  
    {  
      return shape.YPosition + shape.Height;  
    }  
  
    public static double Top(this IShape shape)  
    {  
      return shape.YPosition;  
    }  
  
    public static double Left(this IShape shape)  
    {  
      return shape.XPosition;  
    }  
  
    public static double Right(this IShape shape)  
    {  
      return shape.XPosition + shape.Width;  
    }  
  
    public static void AlignYCenter(this IShape shape, double Y)  
    {  
      shape.Move(shape.XPosition, Y - shape.YCenter());  
    }  
  
    public static void AlignXCenter(this IShape shape, double X)  
    {  
      shape.Move(X - shape.XCenter(), shape.YPosition);  
    }  
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double YCenter(this IShape shape)  
    {  
        return shape.Height / 2.0;  
    }   
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double XCenter(this IShape shape)  
    {  
        return shape.Width / 2.0;  
    }  
  }  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md)   
 [Przykład: Połączenia kształtów na diagramie polecenia menu](http://go.microsoft.com/fwlink/?LinkId=213809)   
 [Przykład: Tworzenie elementów, kształty i Stereotypy](http://go.microsoft.com/fwlink/?LinkId=213811)
