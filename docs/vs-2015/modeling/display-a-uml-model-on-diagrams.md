---
title: Wyświetlanie modelu UML na diagramach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06a22161068dd7604fe7bb4153e322c0954b89d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533021"
---
# <a name="display-a-uml-model-on-diagrams"></a>Wyświetlanie modelu UML na diagramach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W kodzie programu rozszerzenia do programu Visual Studio można kontrolować sposób wyświetlania elementów modelu na diagramach. Aby sprawdzić, które wersje programu Visual Studio obsługują modele UML, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

W tym temacie:
- [Aby wyświetlić element na diagramie](#Display)

- [Uzyskiwanie dostępu do kształtów reprezentujących element](#GetShapes)

- [Przesuwanie i zmiana rozmiarów kształtów](#Moving)

- [Aby usunąć kształt z diagramu](#Removing)

- [Otwieranie i tworzenie diagramów](#Opening)

- [Przykład: polecenie do wyrównywania kształtów](#AlignCommand)

## <a name="to-display-an-element-on-a-diagram"></a><a name="Display"></a> Aby wyświetlić element na diagramie
 Podczas tworzenia elementu, takiego jak przypadek użycia lub Akcja, użytkownik może zobaczyć go w Eksploratorze modelu UML, ale nie zawsze jest automatycznie wyświetlany na diagramie. W niektórych przypadkach należy napisać kod, aby go wyświetlić. W poniższej tabeli zestawiono alternatywy.

|Typ elementu|Na przykład|Aby wyświetlić ten kod, należy|
|---------------------|-----------------|-------------------------------------|
|Klasyfikator|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|Utwórz skojarzone kształty na określonych diagramach. Dla każdego klasyfikatora można utworzyć dowolną liczbę kształtów.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> Ustaw `parentShape` na `null` dla kształtu na najwyższym poziomie diagramu.<br /><br /> Aby wyświetlić jeden kształt w innym:<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);`**Uwaga:**  W przypadku wykonywania w ramach transakcji **ILinkedUndo** , Metoda czasami zwraca wartość nie `IShape` . Ale kształt jest prawidłowo tworzony i jest dostępny za pomocą `IElement.Shapes().`|
|Element podrzędny klasyfikatora|Atrybut, operacja,<br /><br /> Część, port|Automatyczny — żaden kod nie jest wymagany.<br /><br /> Jest on wyświetlany jako część elementu nadrzędnego.|
|Zachowanie|Interakcja (sekwencja),<br /><br /> Działanie|Powiąż zachowanie z odpowiednim diagramem.<br /><br /> Każde zachowanie może być powiązane z co najwyżej jednym diagramem naraz.<br /><br /> Na przykład:<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|
|Element podrzędny zachowania|Linie życia, komunikaty, akcje, węzły obiektów|Automatyczny — żaden kod nie jest wymagany.<br /><br /> Jest wyświetlana, jeśli element nadrzędny jest powiązany z diagramem.|
|Relacja|Skojarzenie, Generalizacja, przepływ, zależność|Automatyczny — żaden kod nie jest wymagany.<br /><br /> Jest on wyświetlany na każdym diagramie, na którym są wyświetlane oba punkty końcowe.|

## <a name="accessing-the-shapes-that-represent-an-element"></a><a name="GetShapes"></a> Uzyskiwanie dostępu do kształtów reprezentujących element
 Kształt reprezentujący element należy do typów:

 `IShape`

 `IShape<`*ElementType*`>`

 Where *ElementType* jest typem elementu modelu, takim jak `IClass` lub `IUseCase` .

|Składnia|Opis|
|-|-|
|`anElement.Shapes ()`|Wszystkie `IShapes` reprezentujące ten element w otwartych diagramach.|
|`anElement.Shapes(aDiagram)`|Wszystkie `IShapes` reprezentujące ten element na określonym diagramie.|
|`anIShape.GetElement()`|Ten `IElement` kształt reprezentuje. Zwykle należy rzutować go do podklasy IElement.|
|`anIShape.Diagram`|`IDiagram`Zawiera kształt.|
|`anIShape.ParentShape`|Kształt, który zawiera `anIShape` . Na przykład kształt portu jest zawarty w obrębie kształtu składnika.|
|`anIShape.ChildShapes`|Kształty zawarte w `IShape` lub `IDiagram` .|
|`anIShape.GetChildShapes<IUseCase>()`|Kształty zawarte w `IShape` lub `IDiagram` reprezentujące elementy określonego typu, na przykład `IUseCase` .|
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|Rzutowanie ogólnego `IShape` na silnie wpisane `IShape<IElement>` .|
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|Rzutowanie kształtu z jednego sparametryzowanego typu kształtu na inny.|

## <a name="moving-and-resizing-shapes"></a><a name="Moving"></a> Przesuwanie i zmiana rozmiarów kształtów

|Składnia|Opis|
|-|-|
|`anIShape.Move(x, y, [width], [height])`|Przenoszenie lub zmiana rozmiaru kształtu.|
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|Aktywuj okno i przewiń diagram, aby wyświetlić wszystkie pożądane kształty. Wszystkie kształty muszą znajdować się na diagramie. Jeśli `zoomToFit` ma wartość true, diagram zostanie w razie potrzeby skalowany w taki sposób, aby wszystkie kształty były widoczne.|

 Aby zapoznać się z przykładem, zobacz [Definiowanie wyrównania polecenia](#AlignCommand).

## <a name="to-remove-a-shape-from-a-diagram"></a><a name="Removing"></a> Aby usunąć kształt z diagramu
 Można usunąć kształty niektórych typów elementów bez usuwania elementu.

|Element modelu|Aby usunąć kształt|
|-------------------|-------------------------|
|Klasyfikator: Klasa, interfejs, Wyliczenie, aktor, przypadek użycia lub składnik|`shape.Delete();`|
|Zachowanie: interakcja lub działanie|Możesz usunąć diagram z projektu. Użyj, `IDiagram.FileName` Aby uzyskać ścieżkę.<br /><br /> Nie spowoduje to usunięcia zachowania z modelu.|
|Dowolny inny kształt|Nie można jawnie usunąć innych kształtów z diagramu. Kształt zostanie automatycznie ukryty, jeśli element zostanie usunięty z modelu lub jeśli kształt nadrzędny zostanie usunięty z diagramu.|

## <a name="opening-and-creating-diagrams"></a><a name="Opening"></a> Otwieranie i tworzenie diagramów

### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>Aby uzyskać dostęp do bieżącego diagramu użytkownika z rozszerzenia polecenia lub gestu
 Zadeklaruj tę zaimportowaną właściwość w klasie:

 `[Import]`

 `IDiagramContext Context { get; set; }`

 W metodzie, uzyskaj dostęp do diagramu:

 `IClassDiagram classDiagram =`

 `Context.CurrentDiagram as IClassDiagram;`

> [!NOTE]
> Wystąpienie `IDiagram` (i jego podtypy, takie jak `IClassDiagram` ) jest prawidłowe tylko w trakcie przetwarzania polecenia. Nie zaleca się zachowywania `IDiagram` obiektu w zmiennej, która utrzymuje się, gdy kontrolka jest zwracana do użytkownika.

 Aby uzyskać więcej informacji, zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

### <a name="to-obtain-a-list-of-open-diagrams"></a>Aby uzyskać listę otwartych diagramów
 Lista diagramów, które są aktualnie otwarte w projekcie:

```
Context.CurrentDiagram.ModelStore.Diagrams()
```

## <a name="to-access-the-diagrams-in-a-project"></a>Aby uzyskać dostęp do diagramów w projekcie
 Za [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pomocą interfejsu API można otwierać i tworzyć projekty i diagramy modelowania.

 Zwróć uwagę na rzutowanie z `EnvDTE.ProjectItem` do `IDiagramContext` .

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

 Wystąpienia `IDiagram` i jego podtypy są nieprawidłowe po powrocie kontroli do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Można również uzyskać Magazyn modeli z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu:

```

      Project project = ...;
IModelStore modelStore = (project as IModelingProject).Store;
```

## <a name="example-command-for-aligning-shapes"></a><a name="AlignCommand"></a> Przykład: polecenie do wyrównywania kształtów
 Poniższy kod implementuje polecenie menu, które dopasowuje kształty w sposób starannie. Użytkownik musi najpierw umieścić dwa lub więcej kształtów w przybliżonym wyrównaniu, w pionie lub w poziomie. Następnie Wyrównaj polecenie może służyć do wyrównywania ich centrów.

 Aby udostępnić polecenie, Dodaj ten kod do projektu polecenia menu, a następnie wdróż to rozszerzenie na użytkownikach. Aby uzyskać więcej informacji, zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

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
  // See https://msdn.microsoft.com/library/ee329481.aspx

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension] // TODO: Add other diagram types if needed
  class CommandExtension : ICommandExtension
  {
    /// <summary>
    /// See https://msdn.microsoft.com/library/ee329481.aspx
    /// </summary>
    [Import]
    IDiagramContext context { get; set; }

    /// <summary>
    /// Transaction context.
    /// See https://msdn.microsoft.com/library/ee330926.aspx
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
 [Poszerzanie modeli UML i diagramów](../modeling/extend-uml-models-and-diagrams.md) [nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md)
 