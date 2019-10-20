---
title: Dodawanie poleceń i gestów do diagramów warstwowych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom commands
- layer diagrams, adding custom gestures
ms.assetid: ac9c417b-0b40-4a90-86f5-ee3cbdce030b
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7b0c54975cdd5bc86f77dddbd5ca1a56c1896394
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655318"
---
# <a name="add-commands-and-gestures-to-layer-diagrams"></a>Dodawanie poleceń i gestów do diagramów warstw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można definiować polecenia menu kontekstowego i programy obsługi gestów. Można spakować te rozszerzenia w rozszerzeniu integracji programu Visual Studio (VSIX), które można dystrybuować do innych użytkowników programu Visual Studio.

 Jeśli chcesz, możesz zdefiniować kilka poleceń i programów obsługi gestów w tym samym projekcie programu Visual Studio. Można także połączyć kilka takich projektów w jeden VSIX. Można na przykład zdefiniować pojedynczy VSIX, który zawiera polecenia warstwy, język specyficzny dla domeny i polecenia dla diagramów UML.

> [!NOTE]
> Możesz również dostosować sprawdzanie poprawności architektury, w którym kod źródłowy użytkowników jest porównywany z diagramami warstw. Sprawdzanie poprawności architektury należy zdefiniować w osobnym projekcie programu Visual Studio. Możesz dodać go do tego samego VSIX jako inne rozszerzenia. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowej walidacji architektury do diagramów warstwowych](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Wymagania
 Zobacz [wymagania](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Definiowanie polecenia lub gestu w nowym VSIX
 Najszybszą metodą tworzenia rozszerzenia jest użycie szablonu projektu. Spowoduje to umieszczenie kodu i manifestu VSIX w tym samym projekcie.

#### <a name="to-define-an-extension-by-using-a-project-template"></a>Aby zdefiniować rozszerzenie przy użyciu szablonu projektu

1. Utwórz projekt w nowym rozwiązaniu za pomocą polecenia **Nowy projekt** w menu **plik** .

2. W oknie dialogowym **Nowy projekt** w obszarze **projekty modelowania**wybierz **rozszerzenie poleceń projektanta warstwy** lub **rozszerzenie gestu projektanta warstwy**.

    Szablon tworzy projekt zawierający mały przykład pracy.

3. Aby przetestować rozszerzenie, naciśnij **klawisze CTRL + F5** lub **F5**.

    Zostanie uruchomione doświadczalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. W tym przypadku Utwórz diagram warstwowy. Rozszerzenie polecenia lub gestu powinno być wykonane na tym diagramie.

4. Zamknij wystąpienie eksperymentalne i zmodyfikuj przykładowy kod. Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modeli warstw w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md).

5. Do tego samego projektu można dodać więcej obsługi poleceń lub gestów. Aby uzyskać więcej informacji, zobacz jedną z następujących sekcji:

    [Definiowanie polecenia menu](#command)

    [Definiowanie procedury obsługi gestu](#gesture)

6. Aby zainstalować rozszerzenie w głównym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub na innym komputerze, Znajdź plik **. vsix** w polu *bin \\* . Skopiuj go do komputera, na którym chcesz go zainstalować, a następnie kliknij go dwukrotnie. Aby go odinstalować, użyj **rozszerzeń i aktualizacji** w menu **Narzędzia** .

## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Dodawanie polecenia lub gestu do oddzielnego VSIX
 Jeśli chcesz utworzyć jeden VSIX zawierający polecenia, moduły sprawdzania warstwy i inne rozszerzenia, zalecamy utworzenie jednego projektu do definiowania VSIX i oddzielnych projektów dla programów obsługi. Aby uzyskać informacje o innych typach rozszerzeń modelowania, zobacz [Rozszerzanie modeli UML i diagramów](../modeling/extend-uml-models-and-diagrams.md).

#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Aby dodać rozszerzenia warstwy do oddzielnego VSIX

1. Utwórz projekt biblioteki klas w nowym lub istniejącym rozwiązaniu programu Visual Studio. W oknie dialogowym **Nowy projekt** kliknij pozycję **Wizualizacja C#**  , a następnie kliknij pozycję **Biblioteka klas**. Ten projekt będzie zawierać polecenia lub klasy obsługi gestów.

    > [!NOTE]
    > Istnieje możliwość zdefiniowania więcej niż jednego polecenia lub klasy obsługi gestów w jednej bibliotece klas, ale należy zdefiniować klasy walidacji warstwy w oddzielnej bibliotece klas.

2. Zidentyfikuj lub Utwórz projekt VSIX w rozwiązaniu. Projekt VSIX zawiera plik o nazwie **source. Extension. vsixmanifest**. Aby dodać projekt VSIX:

    1. W oknie dialogowym **Nowy projekt** rozwiń **element Wizualizacja C#** , a następnie kliknij pozycję **rozszerzalność**, a następnie kliknij pozycję **Projekt VSIX**.

    2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt VSIX, a następnie kliknij pozycję **Ustaw jako projekt startowy**.

    3. Kliknij pozycję **Wybierz wersje** i upewnij się, że jest zaznaczone pole wyboru **Visual Studio** .

3. W polu **source. Extension. vsixmanifest**w obszarze **zasoby**Dodaj polecenie lub projekt programu obsługi gestów jako składnik MEF.

    1. Na karcie **zasoby**kliknij pozycję **Nowy**.

    2. W obszarze **Typ**wybierz pozycję **Microsoft. VisualStudio. MefComponent**.

    3. W obszarze **Źródło**wybierz pozycję **projekt w bieżącym rozwiązaniu** , a następnie wybierz nazwę projektu polecenia lub programu obsługi gestów.

    4. Zapisz plik.

4. Wróć do projektu obsługi polecenia lub gestu i Dodaj następujące odwołania do projektu.

|**Tematy pomocy**|**Co można zrobić**|
|-------------------|------------------------------------|
|Program Files\Microsoft Visual Studio [wersja] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Tworzenie i Edytowanie warstw|
|Microsoft. VisualStudio. UML. Interfaces|Tworzenie i Edytowanie warstw|
|Microsoft. VisualStudio. ArchitectureTools. rozszerzalność|Modyfikuj kształty na diagramach|
|System. ComponentModel. kompozycji|Definiuj składniki przy użyciu Managed Extensibility Framework (MEF)|
|Microsoft. VisualStudio. Modeling. Sdk. nowszym|Definiowanie rozszerzeń modelowania|
|Microsoft. VisualStudio. Modeling. Sdk. diagramy. nowszym|Aktualizowanie kształtów i diagramów|

1. Edytuj plik klasy w projekcie biblioteki C# klas, aby zawierał kod dla rozszerzenia. Aby uzyskać więcej informacji, zobacz jedną z następujących sekcji:

     [Definiowanie polecenia menu](#command)

     [Definiowanie procedury obsługi gestu](#gesture)

     Zobacz również [nawigowanie i aktualizowanie modeli warstw w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md).

2. Aby przetestować tę funkcję, naciśnij klawisze CTRL + F5 lub F5. Zostanie otwarte doświadczalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. W tym wystąpieniu Utwórz lub Otwórz diagram warstwowy.

3. Aby zainstalować VSIX w głównym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub na innym komputerze, Znajdź plik **. vsix** w katalogu **bin** projektu VSIX. Skopiuj go do komputera, na którym chcesz zainstalować VSIX. Kliknij dwukrotnie plik VSIX w Eksploratorze Windows (Eksplorator plików w systemie Windows 8).

     Aby go odinstalować, użyj **rozszerzeń i aktualizacji** w menu **Narzędzia** .

## <a name="command"></a>Definiowanie polecenia menu
 Można dodać więcej definicji poleceń menu do istniejącego gestu lub projektu polecenia. Każde polecenie jest zdefiniowane przez klasę, która ma następujące cechy:

- Klasa jest zadeklarowana w następujący sposób:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`*MyLayerCommand* `: ICommandExtension { ... }`

- Przestrzeń nazw i nazwa klasy są nieważne.

- Metody implementujące `ICommandExtension` są następujące:

  - `string Text {get;}` — etykieta, która pojawia się w menu.

  - `void QueryStatus(IMenuCommand command)`-wywoływana, gdy użytkownik kliknie prawym przyciskiem myszy diagram i określi, czy polecenie powinno być widoczne i włączone dla bieżącego zaznaczenia użytkownika.

  - `void Execute(IMenuCommand command)`-wywoływana, gdy użytkownik wybierze polecenie.

- Aby określić bieżące zaznaczenie, można zaimportować `IDiagramContext`:

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

  Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modeli warstw w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md).

  Aby dodać nowe polecenie, Utwórz nowy plik kodu zawierający Poniższy przykład. Następnie przetestuj i Edytuj.

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for Layer diagrams:
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

## <a name="gesture"></a>Definiowanie procedury obsługi gestu
 Procedura obsługi gestu reaguje, gdy użytkownik przeciągnie elementy na diagram warstwy i gdy użytkownik kliknie dwukrotnie dowolne miejsce na diagramie.

 Do istniejącego polecenia lub projektu VSIX obsługi gestu można dodać plik kodu, który definiuje procedurę obsługi gestu:

```
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

- Elementy `IGestureExtension` są następujące:

   **OnDoubleClick** — wywoływana, gdy użytkownik kliknie dwukrotnie dowolne miejsce na diagramie.

   **CanDragDrop** — wielokrotnie wywoływana, gdy użytkownik przesuwa mysz podczas przeciągania elementu na diagram. Musi ona szybko współpracować.

   **OnDragDrop** — wywoływana, gdy użytkownik porzuca element na diagramie.

- Pierwszym argumentem każdej metody jest `IShape`, z którego można uzyskać element warstwy. Na przykład:

  ```
  public void OnDragDrop(IShape target, IDataObject data)
  {
      ILayerElement element = target.GetLayerElement();
      if (element is ILayer)
      {
          // ...
      }
  }
  ```

- Procedury obsługi dla niektórych typów przeciąganego elementu są już zdefiniowane. Na przykład użytkownik może przeciągać elementy z Eksplorator rozwiązań na diagram warstwowy. Nie można zdefiniować procedury obsługi przeciągania dla tego typu elementu. W takich przypadkach metody `DragDrop` nie będą wywoływane.

  Aby uzyskać więcej informacji na temat dekodowania innych elementów, gdy są one przeciągane na diagram, zobacz [Definiowanie obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="see-also"></a>Zobacz też
 [Nawigowanie i aktualizowanie modeli warstw w programie kod programu](../modeling/navigate-and-update-layer-models-in-program-code.md) [Dodawanie niestandardowej walidacji architektury do diagramów warstwowych](../modeling/add-custom-architecture-validation-to-layer-diagrams.md) [Definiowanie i Instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md)
