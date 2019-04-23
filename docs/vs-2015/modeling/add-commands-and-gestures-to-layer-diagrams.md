---
title: Dodawanie poleceń i gestów do diagramów warstw | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom commands
- layer diagrams, adding custom gestures
ms.assetid: ac9c417b-0b40-4a90-86f5-ee3cbdce030b
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 449e273659df1e3b6846ff8e7e3d8d6943ba69f4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079827"
---
# <a name="add-commands-and-gestures-to-layer-diagrams"></a>Dodawanie poleceń i gestów do diagramów warstw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zdefiniować polecenia w menu kontekstowym i elemencie obsługi gestu na diagramach warstwy w programie Visual Studio. Można spakować te rozszerzenia w Visual Studio Integration rozszerzenie (VSIX), którą można dystrybuować do innych użytkowników programu Visual Studio.  
  
 Jeśli chcesz, możesz zdefiniować kilka poleceń i elementów obsługi gestów w tym samym projekcie programu Visual Studio. Możesz również połączyć kilka takich projektów w jeden VSIX. Na przykład można zdefiniować pojedynczy VSIX, zawierający polecenia dotyczące warstwy, języka specyficznego dla domeny i poleceń do diagramów UML.  
  
> [!NOTE]
>  Można również dostosować sprawdzanie poprawności architektury, w źródle użytkowników, których kod jest porównywane z diagramami warstwy. Sprawdzanie poprawności architektury należy zdefiniować w osobnym projekcie programu Visual Studio. Można go dodać do samego VSIX jako inne rozszerzenia. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowej walidacji architektury do diagramów warstw](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
## <a name="requirements"></a>Wymagania  
 Zobacz [wymagania](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Definiowanie polecenia lub gestu w nowym VSIX  
 Najszybszą metodą tworzenia rozszerzenia jest użycie szablonu projektu. Te umieszcza kod i manifestu VSIX w tym samym projekcie.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>Aby zdefiniować rozszerzenie przy użyciu szablonu projektu  
  
1. Tworzenie projektu w nowym rozwiązaniu za pomocą **nowy projekt** polecenie **pliku** menu.  
  
2. W **nowy projekt** dialogowego **projekty modelowania**, wybierz opcję **rozszerzenia polecenia projektanta warstwy** lub **rozszerzenia gestu projektanta warstwy** .  
  
    Ten szablon tworzy projekt zawierający krótki przykład roboczy.  
  
3. Aby przetestować rozszerzenie, naciśnij klawisz **kombinację klawiszy CTRL + F5** lub **F5**.  
  
    Eksperymentalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoczyna się. W tym wypadku Utwórz diagram warstwy. Rozszerzenia poleceń lub gest powinny działać na tym diagramie.  
  
4. Zamknij wystąpienie doświadczalne i Modyfikuj przykładowy kod. Aby uzyskać więcej informacji, zobacz [Navigate i aktualizacji warstwy modeli w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
5. Możesz dodać więcej programów obsługi polecenia lub gestu w tym samym projekcie. Aby uzyskać więcej informacji zobacz jeden z następujących sekcji:  
  
    [Definiowanie polecenia Menu](#command)  
  
    [Definiowanie procedury obsługi gestu](#gesture)  
  
6. Aby zainstalować rozszerzenie w głównym wystąpieniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], lub na innym komputerze, należy znaleźć **.vsix** w pliku *bin\\*. Skopiuj go na komputerze, na którym chcesz go zainstalować i kliknij go dwukrotnie. Aby odinstalować go, należy użyć **rozszerzenia i aktualizacje** na **narzędzia** menu.  
  
## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Dodawanie polecenia lub gestu do oddzielnych VSIX  
 Jeśli chcesz utworzyć jeden VSIX zawierający polecenia, moduły sprawdzania warstwy oraz inne rozszerzenia, zaleca się utworzenie jednego projektu do definiowania VSIX i oddzielnych projektów dla programów obsługi. Aby uzyskać informacje na temat innych rodzajów rozszerzenia modelowania, zobacz [modeli i diagramów UML rozszerzyć](../modeling/extend-uml-models-and-diagrams.md).  
  
#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Aby dodać rozszerzenia warstwy do oddzielnego VSIX  
  
1. Utwórz projekt biblioteki klas w nowym lub istniejącym rozwiązaniu Visual Studio. W **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#** a następnie kliknij przycisk **biblioteki klas**. Ten projekt będzie zawierać polecenia lub gest klasy programu obsługi.  
  
    > [!NOTE]
    >  Można zdefiniować więcej niż jednej klasy programu obsługi polecenia lub gestu w jednej bibliotece klasy, ale należy zdefiniować warstwy sprawdzania poprawności klas w bibliotece osobnej klasy.  
  
2. Identyfikowanie lub Utwórz projekt VSIX w rozwiązaniu. Projekt VSIX zawiera plik o nazwie **source.extension.vsixmanifest**. Aby dodać projekt VSIX:  
  
    1. W **nowy projekt** okna dialogowego rozwiń **Visual C#**, następnie kliknij przycisk **rozszerzalności**, a następnie kliknij przycisk **projekt VSIX**.  
  
    2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt VSIX, a następnie kliknij przycisk **Ustaw jako projekt startowy**.  
  
    3. Kliknij przycisk **Wybierz wersje** i upewnij się, że **programu Visual Studio** jest zaznaczone.  
  
3. W **source.extension.vsixmanifest**w obszarze **zasoby**, Dodaj polecenie lub projekt obsługi gestu jako składnik MEF.  
  
    1. W **zasoby**karcie Wybierz **New**.  
  
    2. W **typu**, wybierz opcję **Microsoft.VisualStudio.MefComponent**.  
  
    3. W **źródła**, wybierz opcję **projekt w bieżącym rozwiązaniu** i wybierz nazwę projektu obsługi polecenia lub gestu.  
  
    4. Zapisz plik.  
  
4. Wróć do projektu obsługi polecenia lub gestu i dodaj następujące odwołania do projektu.  
  
|**Dokumentacja**|**Co to pozwala zrobić**|  
|-------------------|------------------------------------|  
|Program Files\Microsoft Visual Studio [wersja] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Utwórz i Edytuj warstwy|  
|Microsoft.VisualStudio.Uml.Interfaces|Utwórz i Edytuj warstwy|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Modyfikowanie kształtów na diagramach|  
|System.ComponentModel.Composition|Zdefiniuj składniki za pomocą Managed Extensibility Framework (MEF)|  
|Microsoft.VisualStudio.Modeling.Sdk.[version]|Zdefiniuj rozszerzenia modelowania|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]|Zaktualizuj kształty i diagramy|  
  
1. Edytuj plik klasy w języku C# projekt biblioteki klas zawiera kod dla rozszerzenia. Aby uzyskać więcej informacji zobacz jeden z następujących sekcji:  
  
     [Definiowanie polecenia Menu](#command)  
  
     [Definiowanie procedury obsługi gestu](#gesture)  
  
     Zobacz też [Navigate i aktualizacji warstwy modeli w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
2. Aby przetestować funkcję, naciśnij kombinację klawiszy CTRL + F5 lub F5. Eksperymentalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zostanie otwarty. W tym wypadku Utwórz lub Otwórz diagram warstwy.  
  
3. Aby zainstalować VSIX w głównym wystąpieniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], lub na innym komputerze, należy znaleźć **.vsix** w pliku **bin** katalogu projektów VSIX. Skopiuj go do komputera, na którym chcesz zainstalować VSIX. Kliknij dwukrotnie plik VSIX w programie Windows Explorer (Eksplorator plików w systemie Windows 8).  
  
     Aby odinstalować go, należy użyć **rozszerzenia i aktualizacje** na **narzędzia** menu.  
  
## <a name="command"></a> Definiowanie polecenia Menu  
 Możesz dodać więcej definicji poleceń menu do istniejącego gest lub polecenia projektu. Każde polecenie jest zdefiniowane przez klasę, która ma następujące cechy:  
  
- Klasa jest zadeklarowana w następujący sposób:  
  
   `[LayerDesignerExtension]`  
  
   `[Export(typeof(ICommandExtension))]`  
  
   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`  
  
- Przestrzeń nazw i nazwę klasy nie są ważne.  
  
- Metody, które implementują `ICommandExtension` są następujące:  
  
  - `string Text {get;}` Etykieta jest wyświetlana w menu.  
  
  - `void QueryStatus(IMenuCommand command)` -wywoływana, gdy użytkownik kliknie prawym przyciskiem myszy diagram i określa, czy polecenie powinno być widoczne i włączone dla bieżącego zaznaczenia przez użytkownika.  
  
  - `void Execute(IMenuCommand command)` -wywoływana, gdy użytkownik wybierze polecenie.  
  
- Aby określić bieżące zaznaczenie, można importować `IDiagramContext`:  
  
   `[Import]`  
  
   `public IDiagramContext DiagramContext { get; set; }`  
  
   `...`  
  
   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`  
  
  Aby uzyskać więcej informacji, zobacz [Navigate i aktualizacji warstwy modeli w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
  Aby dodać nowe polecenie, Utwórz nowy plik kodu, który zawiera poniższy przykład. Następnie przetestuj i edytuj go.  
  
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
  
## <a name="gesture"></a> Definiowanie procedury obsługi gestu  
 Obsługa gestu reaguje, gdy użytkownik przeciągnie elementy na diagram warstwy, a użytkownik kliknie dwukrotnie dowolne miejsce na diagramie.  
  
 Do istniejącego polecenia lub projektu VSIX obsługi gestu można dodać pliku z kodem, który definiuje procedury obsługi gestu:  
  
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
  
 Zwróć uwagę na następujące kwestie dotyczące obsługi gestu:  
  
- Elementy członkowskie `IGestureExtension` są następujące:  
  
   **OnDoubleClick** -wywoływana, gdy użytkownik kliknie dwukrotnie dowolne miejsce na diagramie.  
  
   **CanDragDrop** — wywoływany wielokrotnie, gdy użytkownik przesuwa mysz podczas przeciągania elementu na diagram. Musi działać szybko.  
  
   **OnDragDrop** -wywoływana, gdy użytkownik porzuca element na diagram.  
  
- Pierwszy argument do każdej metody jest `IShape`, z którego można uzyskać element warstwy. Na przykład:  
  
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
  
- Programy obsługi dla niektórych typów przeciąganych elementów zostały już zdefiniowane. Na przykład użytkownik może przeciągać elementy z Eksploratora rozwiązań na diagram warstwy. Nie można zdefiniować uchwytu przeciągania dla tego typu elementu. W takich przypadkach Twoje `DragDrop` metody nie zostaną wywołane.  
  
  Aby uzyskać więcej informacji dotyczących sposobu dekodowania innych elementów podczas przeciągania ich na diagram, zobacz [definiowanie procedury obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modeli warstw w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md)   
 [Dodawanie niestandardowej walidacji architektury do diagramów warstw](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Definiowanie i instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md)
