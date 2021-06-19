---
title: Dodawanie poleceń i gestów do diagramów zależności
description: Dowiedz się, jak definiować polecenia menu dostępne po kliknięciu prawym przyciskiem myszy i procedury obsługi gestów na diagramach zależności w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 43d6cf5410aed3d79814d5304705a424bcc71e89
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387453"
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Dodawanie poleceń i gestów do diagramów zależności

Możesz zdefiniować polecenia menu dostępne po kliknięciu prawym przyciskiem myszy i procedury obsługi gestów na diagramach zależności w Visual Studio. Rozszerzenia te można spakować w Visual Studio Integration Extension (VSIX), które można rozpowszechniać wśród innych Visual Studio użytkowników.

W tym samym projekcie można zdefiniować kilka programów obsługi poleceń i gestów Visual Studio, jeśli chcesz. Można również połączyć kilka takich projektów w jeden vsix. Można na przykład zdefiniować pojedynczy vsix, który zawiera polecenia warstwy i język specyficzny dla domeny.

> [!NOTE]
> Można również dostosować weryfikację architektury, w której kod źródłowy użytkowników jest porównywany z diagramami zależności. Walidację architektury należy zdefiniować w oddzielnym Visual Studio projektu. Możesz dodać go do tego samego vsix co inne rozszerzenia. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowej weryfikacji architektury do diagramów zależności.](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

## <a name="requirements"></a>Wymagania

Zobacz [Wymagania.](../modeling/extend-layer-diagrams.md#requirements)

## <a name="define-a-command-or-gesture-in-a-new-vsix"></a>Definiowanie polecenia lub gestu w nowym vsix

Najszybszą metodą tworzenia rozszerzenia jest użycie szablonu projektu. Dzięki temu kod i manifest VSIX są umieszczane w tym samym projekcie.

1. Utwórz nowy projekt **Rozszerzenie poleceń projektanta** warstwy lub **Rozszerzenie gestu projektanta** warstw.

   Szablon tworzy projekt zawierający mały przykład roboczy.

2. Aby przetestować rozszerzenie, naciśnij **klawisze Ctrl** + **F5** **lub F5.**

    Uruchamia się eksperymentalne wystąpienie Visual Studio. W tym przypadku utwórz diagram zależności. Rozszerzenie polecenia lub gestu powinno działać na tym diagramie.

3. Zamknij wystąpienie eksperymentalne i zmodyfikuj przykładowy kod.

4. Do tego samego projektu można dodać więcej programów obsługi poleceń lub gestów. Aby uzyskać więcej informacji, zobacz jedną z następujących sekcji:

    [Definiowanie polecenia menu](#command)

    [Definiowanie procedury obsługi gestów](#gesture)

::: moniker range="vs-2017"

5. Aby zainstalować rozszerzenie w głównym wystąpieniu Visual Studio lub na innym komputerze, znajdź plik *vsix* w *katalogu bin.* Skopiuj go na komputer, na którym chcesz go zainstalować, a następnie kliknij go dwukrotnie. Aby go odinstalować, **wybierz pozycję Rozszerzenia i aktualizacje** w menu Narzędzia. 

::: moniker-end

::: moniker range=">=vs-2019"

5. Aby zainstalować rozszerzenie w głównym wystąpieniu Visual Studio lub na innym komputerze, znajdź plik *vsix* w *katalogu bin.* Skopiuj go na komputer, na którym chcesz go zainstalować, a następnie kliknij go dwukrotnie. Aby go odinstalować, wybierz **pozycję Zarządzaj rozszerzeniami** w menu **Rozszerzenia.**

::: moniker-end

## <a name="add-a-command-or-gesture-to-a-separate-vsix"></a>Dodawanie polecenia lub gestu do oddzielnego vsix

Jeśli chcesz utworzyć jeden vsix zawierający polecenia, moduły sprawdzania ważności warstw i inne rozszerzenia, zalecamy utworzenie jednego projektu w celu zdefiniowania vsix i oddzielnych projektów dla programów obsługi.

1. Utwórz nowy projekt **Biblioteka** klas. Ten projekt będzie zawierać klasy obsługi poleceń lub gestów.

   > [!NOTE]
   > W jednej bibliotece klas można zdefiniować więcej niż jedną klasę procedury obsługi poleceń lub gestów, ale należy zdefiniować klasy walidacji warstwy w oddzielnej bibliotece klas.

2. Dodaj lub utwórz projekt VSIX w rozwiązaniu. Projekt VSIX zawiera plik o nazwie **source.extension.vsixmanifest.**

3. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt VSIX i wybierz **polecenie Ustaw jako projekt startowy.**

4. W **pliku source.extension.vsixmanifest** w obszarze **Assets** dodaj projekt obsługi poleceń lub gestów jako składnik MEF.

    1. Na karcie **Assets**(Zasoby) wybierz pozycję **New (Nowy).**

    2. W **witrynie Typ** wybierz **pozycję Microsoft.VisualStudio.MefComponent.**

    3. W **źródle** wybierz **pozycję Projekt w bieżącym** rozwiązaniu i wybierz nazwę projektu obsługi poleceń lub gestów.

    4. Zapisz plik.

5. Wróć do projektu obsługi poleceń lub gestów i dodaj następujące odwołania do projektu:

   |**Odwołanie**|**Co to umożliwia**|
   |-|-|
   |Program Files\Microsoft Visual Studio [wersja]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Tworzenie i edytowanie warstw|
   |Microsoft.VisualStudio.Uml.Interfaces|Tworzenie i edytowanie warstw|
   |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Modyfikowanie kształtów na diagramach|
   |System.componentmodel.composition|Definiowanie składników przy użyciu Managed Extensibility Framework (MEF)|
   |Microsoft.VisualStudio.Modeling.Sdk. [wersja]|Definiowanie rozszerzeń modelowania|
   |Microsoft.VisualStudio.Modeling.Sdk.Diagrams. [wersja]|Aktualizowanie kształtów i diagramów|

6. Edytuj plik klasy w projekcie biblioteki klas języka C#, aby zawierał kod rozszerzenia. Aby uzyskać więcej informacji, zobacz jedną z następujących sekcji:

     [Definiowanie polecenia menu](#command)

     [Definiowanie procedury obsługi gestów](#gesture)

7. Aby przetestować tę funkcję, naciśnij **klawisze Ctrl** + **F5** **lub F5.**

   Zostanie otwarte eksperymentalne wystąpienie Visual Studio. W tym przypadku utwórz lub otwórz diagram zależności.

8. Aby zainstalować vsIX w głównym wystąpieniu programu Visual Studio lub na innym komputerze, znajdź plik **vsix** w katalogu **bin** projektu VSIX. Skopiuj go na komputer, na którym chcesz zainstalować vsix. Kliknij dwukrotnie plik VSIX w Eksplorator plików.

## <a name="defining-a-menu-command"></a><a name="command"></a> Definiowanie polecenia menu

Możesz dodać więcej definicji poleceń menu do istniejącego projektu gestu lub polecenia. Każde polecenie jest definiowane przez klasę, która ma następujące cechy:

- Klasa jest zadeklarowana w następujący sposób:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- Przestrzeń nazw i nazwa klasy są nieistotne.

- Metody implementowania `ICommandExtension` są następujące:

  - `string Text {get;}` — etykieta wyświetlana w menu.

  - `void QueryStatus(IMenuCommand command)` — wywoływana, gdy użytkownik kliknie diagram prawym przyciskiem myszy, i określa, czy polecenie powinno być widoczne i włączone dla bieżącego wyboru użytkownika.

  - `void Execute(IMenuCommand command)` — wywoływana, gdy użytkownik wybierze polecenie .

- Aby określić bieżący wybór, możesz `IDiagramContext` zaimportować :

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

Aby dodać nowe polecenie, utwórz nowy plik kodu zawierający następujący przykład. Następnie przetestuj i edytuj go.

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

## <a name="defining-a-gesture-handler"></a><a name="gesture"></a> Definiowanie procedury obsługi gestów

Procedura obsługi gestów reaguje, gdy użytkownik przeciąga elementy na diagram zależności, a użytkownik klika dwukrotnie dowolne miejsce na diagramie.

Do istniejącego projektu VSIX programu obsługi poleceń lub gestów można dodać plik kodu, który definiuje program obsługi gestów:

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

Zwróć uwagę na następujące punkty dotyczące obsługi gestów:

- Elementy członkowskie `IGestureExtension` są następujące:

     **OnDoubleClick** — wywoływana, gdy użytkownik kliknie dwukrotnie dowolne miejsce na diagramie.

     **CanDragDrop** — wywoływana wielokrotnie, gdy użytkownik przesuwa myszą podczas przeciągania elementu do diagramu. Musi działać szybko.

     **OnDragDrop** — wywoływana, gdy użytkownik porzuca element na diagramie.

- Pierwszym argumentem każdej metody jest `IShape` , z którego można pobrać element warstwy . Na przykład:

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

- Programy obsługi dla niektórych typów przeciąganych elementów są już zdefiniowane. Na przykład użytkownik może przeciągać elementy z Eksplorator rozwiązań na diagram zależności. Nie można zdefiniować procedury obsługi przeciągania dla tych typów elementów. W takich przypadkach metody `DragDrop` nie będą wywoływane.

## <a name="see-also"></a>Zobacz też

- [Dodawanie niestandardowej walidacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
