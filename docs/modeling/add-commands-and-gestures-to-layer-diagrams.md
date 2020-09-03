---
title: Dodawanie poleceń i gestów do diagramów zależności
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ff23e07bd6e81b11d94a8256c33b57b4b0c558c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531394"
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Dodawanie poleceń i gestów do diagramów zależności

Możesz definiować polecenia menu prawym przyciskiem myszy i programy obsługi gestów na diagramach zależności w programie Visual Studio. Można spakować te rozszerzenia w rozszerzeniu integracji programu Visual Studio (VSIX), które można dystrybuować do innych użytkowników programu Visual Studio.

Jeśli chcesz, możesz zdefiniować kilka poleceń i programów obsługi gestów w tym samym projekcie programu Visual Studio. Można także połączyć kilka takich projektów w jeden VSIX. Można na przykład zdefiniować pojedynczy VSIX, który zawiera polecenia warstwy i język specyficzny dla domeny.

> [!NOTE]
> Możesz również dostosować sprawdzanie poprawności architektury, w którym kod źródłowy użytkowników jest porównywany z diagramami zależności. Sprawdzanie poprawności architektury należy zdefiniować w osobnym projekcie programu Visual Studio. Możesz dodać go do tego samego VSIX jako inne rozszerzenia. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowej walidacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Wymagania

Zobacz [wymagania](../modeling/extend-layer-diagrams.md#requirements).

## <a name="define-a-command-or-gesture-in-a-new-vsix"></a>Zdefiniuj polecenie lub gest w nowym VSIX

Najszybszą metodą tworzenia rozszerzenia jest użycie szablonu projektu. Spowoduje to umieszczenie kodu i manifestu VSIX w tym samym projekcie.

1. Utwórz nowe **rozszerzenie polecenia projektanta warstwy** lub projekt **rozszerzenia gestu projektanta warstwy** .

   Szablon tworzy projekt zawierający mały przykład pracy.

2. Aby przetestować rozszerzenie, naciśnij **klawisze CTRL** + **F5** lub **F5**.

    Zostanie uruchomione eksperymentalne wystąpienie programu Visual Studio. W tym wystąpieniu Utwórz diagram zależności. Rozszerzenie polecenia lub gestu powinno być wykonane na tym diagramie.

3. Zamknij wystąpienie eksperymentalne i zmodyfikuj przykładowy kod.

4. Do tego samego projektu można dodać więcej obsługi poleceń lub gestów. Aby uzyskać więcej informacji, zobacz jedną z następujących sekcji:

    [Definiowanie polecenia menu](#command)

    [Definiowanie procedury obsługi gestu](#gesture)

::: moniker range="vs-2017"

5. Aby zainstalować rozszerzenie w głównym wystąpieniu programu Visual Studio lub na innym komputerze, Znajdź plik *. vsix* w katalogu *bin* . Skopiuj go do komputera, na którym chcesz go zainstalować, a następnie kliknij go dwukrotnie. Aby go odinstalować, wybierz pozycję **rozszerzenia i aktualizacje** w menu **Narzędzia** .

::: moniker-end

::: moniker range=">=vs-2019"

5. Aby zainstalować rozszerzenie w głównym wystąpieniu programu Visual Studio lub na innym komputerze, Znajdź plik *. vsix* w katalogu *bin* . Skopiuj go do komputera, na którym chcesz go zainstalować, a następnie kliknij go dwukrotnie. Aby go odinstalować, wybierz pozycję **Zarządzaj rozszerzeniami** w menu **rozszerzenia** .

::: moniker-end

## <a name="add-a-command-or-gesture-to-a-separate-vsix"></a>Dodawanie polecenia lub gestu do oddzielnego VSIX

Jeśli chcesz utworzyć jeden VSIX zawierający polecenia, moduły sprawdzania warstwy i inne rozszerzenia, zalecamy utworzenie jednego projektu do definiowania VSIX i oddzielnych projektów dla programów obsługi.

1. Utwórz nowy projekt **biblioteki klas** . Ten projekt będzie zawierać polecenia lub klasy obsługi gestów.

   > [!NOTE]
   > Istnieje możliwość zdefiniowania więcej niż jednego polecenia lub klasy obsługi gestów w jednej bibliotece klas, ale należy zdefiniować klasy walidacji warstwy w oddzielnej bibliotece klas.

2. Dodaj lub Utwórz projekt VSIX w rozwiązaniu. Projekt VSIX zawiera plik o nazwie **source. Extension. vsixmanifest**.

3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt VSIX i wybierz polecenie **Ustaw jako projekt startowy**.

4. W polu **source. Extension. vsixmanifest**w obszarze **zasoby**Dodaj polecenie lub projekt programu obsługi gestów jako składnik MEF.

    1. Na karcie **zasoby**kliknij pozycję **Nowy**.

    2. W obszarze **Typ**wybierz pozycję **Microsoft. VisualStudio. MefComponent**.

    3. W obszarze **Źródło**wybierz pozycję **projekt w bieżącym rozwiązaniu** , a następnie wybierz nazwę projektu polecenia lub programu obsługi gestów.

    4. Zapisz plik.

5. Wróć do projektu obsługi polecenia lub gestu i Dodaj następujące odwołania do projektu:

   |**Odwołanie**|**Co można zrobić**|
   |-|-|
   |Program Files\Microsoft Visual Studio [wersja] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Tworzenie i Edytowanie warstw|
   |Microsoft. VisualStudio. UML. Interfaces|Tworzenie i Edytowanie warstw|
   |Microsoft. VisualStudio. ArchitectureTools. rozszerzalność|Modyfikuj kształty na diagramach|
   |System. ComponentModel. kompozycji|Definiuj składniki przy użyciu Managed Extensibility Framework (MEF)|
   |Microsoft. VisualStudio. Modeling. Sdk. nowszym|Definiowanie rozszerzeń modelowania|
   |Microsoft. VisualStudio. Modeling. Sdk. diagramy. nowszym|Aktualizowanie kształtów i diagramów|

6. Edytuj plik klasy w projekcie biblioteki klas C#, aby zawierał kod dla rozszerzenia. Aby uzyskać więcej informacji, zobacz jedną z następujących sekcji:

     [Definiowanie polecenia menu](#command)

     [Definiowanie procedury obsługi gestu](#gesture)

7. Aby przetestować funkcję, naciśnij klawisz **Ctrl** + **F5** lub **F5**.

   Zostanie otwarte doświadczalne wystąpienie programu Visual Studio. W tym wystąpieniu Utwórz lub Otwórz diagram zależności.

8. Aby zainstalować VSIX w głównym wystąpieniu programu Visual Studio lub na innym komputerze, Znajdź plik **. vsix** w katalogu **bin** projektu VSIX. Skopiuj go do komputera, na którym chcesz zainstalować VSIX. Kliknij dwukrotnie plik VSIX w Eksploratorze plików.

## <a name="defining-a-menu-command"></a><a name="command"></a> Definiowanie polecenia menu

Można dodać więcej definicji poleceń menu do istniejącego gestu lub projektu polecenia. Każde polecenie jest zdefiniowane przez klasę, która ma następujące cechy:

- Klasa jest zadeklarowana w następujący sposób:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- Przestrzeń nazw i nazwa klasy są nieważne.

- Metody, które implementują `ICommandExtension` są następujące:

  - `string Text {get;}` — Etykieta, która pojawia się w menu.

  - `void QueryStatus(IMenuCommand command)` -wywoływana, gdy użytkownik kliknie prawym przyciskiem myszy diagram i określi, czy polecenie powinno być widoczne i włączone dla bieżącego zaznaczenia użytkownika.

  - `void Execute(IMenuCommand command)` -wywoływana, gdy użytkownik wybierze polecenie.

- Aby określić bieżące zaznaczenie, można zaimportować `IDiagramContext` :

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

Aby dodać nowe polecenie, Utwórz nowy plik kodu zawierający Poniższy przykład. Następnie przetestuj i Edytuj.

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for dependency diagrams:
  [LayerDesignerExtension]
  // This feature is a menu command:
  [Export(typeof(ICommandExtension))]
  // Change the class name to your preference:
  public class MyLayerCommand : ICommandExtension
  {
    [Import]
    public IDiagramContext DiagramContext { get; set; }

    [Import]
    public ILinkedUndoContext LinkedUndoContext { get; set; }

    // Menu command label:
    public string Text
    {
      get { return "Duplicate layers"; }
    }

    // Called when the user right-clicks the diagram.
    // Defines whether the command is visible and enabled.
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible =
      command.Enabled = DiagramContext.CurrentDiagram
        .SelectedShapes.Count() > 0;
    }

    // Called when the user selects the command.
    public void Execute(IMenuCommand command)
    {
      // A selection of starting points:
      IDiagram diagram = this.DiagramContext.CurrentDiagram;
      ILayerModel lmodel = diagram.GetLayerModel();
      foreach (ILayer layer in lmodel.Layers)
      { // All layers in model.
      }
      // Updates should be performed in a transaction:
      using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("copy selection"))
      {
        foreach (ILayer layer in
          diagram.SelectedShapes
            .Select(shape=>shape.GetLayerElement())
            .Where(element => element is ILayer))
        {
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");
          // Position the shapes:
          IShape originalShape = layer.GetShape();
          copy.GetShape().Move(
            originalShape.XPosition + originalShape.Width * 1.2,
            originalShape.YPosition);
        }
        t.Commit();
      }
    }
  }
}
```

## <a name="defining-a-gesture-handler"></a><a name="gesture"></a> Definiowanie procedury obsługi gestu

Procedura obsługi gestu reaguje, gdy użytkownik przeciągnie elementy na diagram zależności i gdy użytkownik kliknie dwukrotnie dowolne miejsce na diagramie.

Do istniejącego polecenia lub projektu VSIX obsługi gestu można dodać plik kodu, który definiuje procedurę obsługi gestu:

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtensions // change to your preference
{
  [LayerDesignerExtension]
  [Export(typeof(IGestureExtension))]
  public class MyLayerGestureHandler : IGestureExtension
  {
  }
}
```

Zwróć uwagę na następujące kwestie dotyczące programów obsługi gestu:

- Elementy członkowskie `IGestureExtension` są następujące:

     **OnDoubleClick** — wywoływana, gdy użytkownik kliknie dwukrotnie dowolne miejsce na diagramie.

     **CanDragDrop** — wielokrotnie wywoływana, gdy użytkownik przesuwa mysz podczas przeciągania elementu na diagram. Musi ona szybko współpracować.

     **OnDragDrop** — wywoływana, gdy użytkownik porzuca element na diagramie.

- Pierwszym argumentem każdej metody jest `IShape` , z którego można uzyskać element warstwy. Na przykład:

    ```csharp
    public void OnDragDrop(IShape target, IDataObject data)
    {
        ILayerElement element = target.GetLayerElement();
        if (element is ILayer)
        {
            // ...
        }
    }
    ```

- Procedury obsługi dla niektórych typów przeciąganego elementu są już zdefiniowane. Na przykład użytkownik może przeciągnąć elementy z Eksplorator rozwiązań na diagram zależności. Nie można zdefiniować procedury obsługi przeciągania dla tego typu elementu. W takich przypadkach `DragDrop` metody nie będą wywoływane.

## <a name="see-also"></a>Zobacz też

- [Dodawanie niestandardowej walidacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
