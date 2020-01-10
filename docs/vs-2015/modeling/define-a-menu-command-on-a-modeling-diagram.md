---
title: Definiowanie polecenia menu na diagramie modelowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5dac0a77b47f604ae5a10f4c8bcfb9d54b51f26c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850458"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>Definiowanie polecenia menu w diagramie modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można zdefiniować dodatkowe elementy menu w menu skrótów diagramu UML. Można kontrolować, czy polecenie menu pojawia się i jest włączone w menu skrótów dowolnego elementu na diagramie, i można napisać kod, który jest uruchamiany, gdy użytkownik wybierze element menu. Można spakować te rozszerzenia w rozszerzeniu integracji programu Visual Studio ([VSIX](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)) i przekazać je do innych użytkowników programu Visual Studio.

## <a name="requirements"></a>Wymagania
 Zobacz [wymagania](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="defining-the-menu-command"></a>Definiowanie polecenia menu
 Aby utworzyć polecenie menu dla projektanta UML, należy utworzyć klasę, która definiuje zachowanie polecenia i osadzić klasę w rozszerzeniu integracji programu Visual Studio (VSIX). VSIX działa jako kontener, który może zainstalować polecenie. Istnieją dwie alternatywne metody definiowania polecenia menu:

- **Utwórz polecenie menu w jego własnym VSIX przy użyciu szablonu projektu.** To jest szybka metoda. Użyj go, jeśli nie chcesz łączyć poleceń menu z innymi typami rozszerzeń, takimi jak rozszerzenia walidacji, niestandardowe elementy przybornika lub programy obsługi gestów.

- **Utwórz oddzielne polecenie menu i projekty VSIX.** Użyj tej metody, jeśli chcesz połączyć kilka typów rozszerzeń z tym samym VSIX. Na przykład, jeśli polecenie menu oczekuje modelu do przestrzegania określonych ograniczeń, można osadzić je w tym samym VSIX jako metodę sprawdzania poprawności.

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>Aby utworzyć polecenie menu w jego własnym VSIX

1. W oknie dialogowym **Nowy projekt** w obszarze **projekty modelowania**wybierz pozycję **rozszerzenie polecenia**.

2. Otwórz plik **CS** w nowym projekcie i zmodyfikuj klasę `CommandExtension`, aby zaimplementować polecenie.

    Aby uzyskać więcej informacji, zobacz [implementowanie polecenia menu](#Implementing).

3. Do tego projektu można dodać dodatkowe polecenia, definiując nowe klasy.

4. Przetestuj polecenie menu, naciskając klawisz F5. Aby uzyskać więcej informacji, zobacz [wykonywanie polecenia menu](#Executing).

5. Zainstaluj polecenie menu na innym komputerze przez skopiowanie pliku **bin\\\*\\\*. vsix** skompilowanego przez projekt. Aby uzyskać więcej informacji, zobacz [Instalowanie i odinstalowywanie rozszerzenia](#Installing).

   Oto alternatywna procedura:

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>Aby utworzyć polecenie menu w oddzielnym projekcie biblioteki klas (DLL)

1. Utwórz projekt biblioteki klas w nowym rozwiązaniu programu Visual Studio lub w istniejącym rozwiązaniu.

   1. W menu **plik** wybierz polecenie **Nowy**, **projekt**.

   2. W obszarze **zainstalowane szablony**wybierz **pozycję C# Visual** lub **Visual Basic**. W środkowej kolumnie Wybierz **Biblioteka klas**.

   3. Ustaw **rozwiązanie** , aby wskazać, czy chcesz utworzyć nowe rozwiązanie, czy dodać składnik do rozwiązania VSIX, które zostało już otwarte.

   4. Ustaw nazwę i lokalizację projektu, a następnie kliknij przycisk OK.

2. Dodaj następujące odwołania do projektu.

   |                                                                                                    Tematy pomocy                                                                                                    |                                                                                                  Co można zrobić                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System.ComponentModel.Composition                                                                                        |                                         Zdefiniuj składniki za pomocą [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).                                          |
   |                                                                                      Microsoft.VisualStudio.Uml.Interfaces                                                                                      |                                                                                        Odczytywanie i zmiana właściwości elementów modelu.                                                                                         |
   |                                                                             Microsoft.VisualStudio.ArchitectureTools.Extensibility                                                                              |                                                                                      Utwórz elementy modelu, Modyfikuj kształty na diagramach.                                                                                       |
   |                                                                                  Microsoft.VisualStudio.Modeling.Sdk.[version]                                                                                  | Zdefiniuj procedury obsługi zdarzeń modelu.<br /><br /> Hermetyzuj serię zmian w modelu. Aby uzyskać więcej informacji, zobacz [łączenie aktualizacji modelu UML przy użyciu transakcji](../modeling/link-uml-model-updates-by-using-transactions.md). |
   |                                                            Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]<br /><br /> (nie zawsze wymagane)                                                             |                                                                                   Dostęp do dodatkowych elementów diagramu dla programów obsługi gestów.                                                                                   |
   | Microsoft. VisualStudio. ArchitectureTools. rozszerzalność. warstwa<br /><br /> Wymagane tylko dla poleceń na diagramach warstwowych. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając diagramy warstwowe](../modeling/extend-layer-diagrams.md). |                                                                                             Zdefiniuj polecenia na diagramie warstwowym.                                                                                              |

3. Dodaj plik klasy do projektu i ustaw jego zawartość na następujący kod.

   > [!NOTE]
   > Zmień przestrzeń nazw, nazwę klasy i wartość zwracaną przez `Text` na preferencję.
   >
   >  W przypadku zdefiniowania wielu poleceń pojawiają się one w menu w kolejności alfabetycznej nazw klas.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Uml.Classes;
       // ADD other UML namespaces if required

   namespace UMLmenu1 // CHANGE
   {
     // DELETE any of these attributes if the command
     // should not appear in some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // All menu commands must export ICommandExtension:
     [Export (typeof(ICommandExtension))]
     // CHANGE class name – determines order of appearance on menu:
     public class Menu1 : ICommandExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       public void QueryStatus(IMenuCommand command)
       { // Set command.Visible or command.Enabled to false
         // to disable the menu command.
         command.Visible = command.Enabled = true;
       }

       public string Text
       {
         get { return "MENU COMMAND LABEL"; }
       }

       public void Execute(IMenuCommand command)
       {
         // A selection of starting points:
         IDiagram diagram = this.DiagramContext.CurrentDiagram;
         foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
         { IElement element = shape.Element; }
         IModelStore modelStore = diagram.ModelStore;
         IModel model = modelStore.Root;
         foreach (IElement element in modelStore.AllInstances<IClass>())
         { }
       }
     }
   }
   ```

    Aby uzyskać więcej informacji o tym, co należy umieścić w metodach, zobacz [implementowanie polecenia menu](#Implementing).

   Należy dodać polecenie menu do projektu VSIX, który działa jako kontener służący do instalowania polecenia. Jeśli chcesz, możesz dołączyć inne składniki do tego samego VSIX.

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>Aby dodać polecenie menu do projektu VSIX

1. Ta procedura nie jest potrzebna, jeśli utworzono polecenie menu z własnym VSIX.

2. Utwórz projekt VSIX, chyba że rozwiązanie już go posiada.

    1. W **Eksplorator rozwiązań**, w menu skrótów rozwiązania, wybierz **Dodaj**, **Nowy projekt**.

    2. W obszarze **zainstalowane szablony**rozwiń **pozycję C# Wizualizacja** lub **Visual Basic**, a następnie wybierz pozycję **rozszerzalność**. W środkowej kolumnie Wybierz pozycję **Projekt VSIX**.

3. W Eksplorator rozwiązań, w menu skrótów projektu VSIX, wybierz **Ustaw jako projekt startowy**.

4. Open **source. Extension. vsixmanifest**.

    1. Na karcie **metadane** Ustaw nazwę VSIX.

    2. Na karcie **Instalowanie obiektów docelowych** Ustaw wersje programu Visual Studio jako elementy docelowe.

    3. Na karcie **zasoby** wybierz pozycję **Nowy**, a następnie w oknie dialogowym Ustaw wartość:

         **Typ** = **składnik MEF**

         **Źródło** = **projektu w bieżącym rozwiązaniu**

         **Projekt** = *projektu biblioteki klas*

## <a name="Implementing"></a>Implementowanie polecenia menu
 Klasa poleceń menu implementuje wymagane metody dla <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>.

|||
|-|-|
|`string Text { get; }`|Zwraca etykietę elementu menu.|
|`void QueryStatus(IMenuCommand command);`|Wywoływana, gdy użytkownik kliknie prawym przyciskiem myszy na diagramie.<br /><br /> Ta metoda nie powinna zmieniać modelu.<br /><br /> Użyj `DiagramContext.CurrentDiagram.SelectedShapes`, aby określić, czy polecenie ma być wyświetlane i włączone.<br /><br /> Zbiór<br /><br /> -   `command.Visible` do `true`, jeśli polecenie musi pojawić się w menu, gdy użytkownik kliknie prawym przyciskiem myszy na diagramie<br />-   `command.Enabled` do `true`, jeśli użytkownik może kliknąć polecenie w menu<br />-   `command.Text`, aby dynamicznie ustawić etykietę menu|
|`void Execute (IMenuCommand command);`|Wywoływana, gdy użytkownik kliknie element menu, jeśli jest widoczny i włączony.|

### <a name="accessing-the-model-in-code"></a>Uzyskiwanie dostępu do modelu w kodzie
 Uwzględnienie następującej deklaracji w klasie poleceń menu:

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 ...

 Deklaracja `IDiagramContext` umożliwia pisanie kodu w metodach, które uzyskują dostęp do diagramu, bieżącego wyboru i modelu:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}
```

### <a name="navigating-and-updating-the-model"></a>Nawigowanie i aktualizowanie modelu
 Elementy modelu UML są dostępne za pomocą interfejsu API. Z bieżącego zaznaczenia lub z katalogu głównego modelu można uzyskać dostęp do wszystkich innych elementów. Aby uzyskać więcej informacji, zobacz [nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md) i [Programowanie przy użyciu interfejsu API UML](../modeling/programming-with-the-uml-api.md).

 Jeśli pracujesz z diagramem sekwencji, zobacz też [Edytowanie diagramów sekwencji UML przy użyciu interfejsu API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Interfejs API pozwala także zmieniać właściwości elementów, usuwać elementy i relacje oraz tworzyć nowe elementy i relacje.

 Domyślnie każda zmiana wprowadzona w metodzie Execute zostanie wykonana w oddzielnej transakcji. Użytkownik będzie mógł cofnąć każdą zmianę osobno. Jeśli chcesz grupować zmiany w pojedynczą transakcję, użyj <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> zgodnie z opisem w temacie [link aktualizacje modelu UML przy użyciu transakcji](../modeling/link-uml-model-updates-by-using-transactions.md).

### <a name="use-the-ui-thread-for-updates"></a>Korzystanie z wątku interfejsu użytkownika dla aktualizacji
 W niektórych przypadkach może być przydatne, aby aktualizować model z wątku w tle. Na przykład jeśli polecenie ładuje dane z powolnego zasobu, można wykonać ładowanie w wątku tła, tak aby użytkownik mógł zobaczyć zmiany w trakcie ich wykonywania, i anulować operację, jeśli jest to konieczne.

 Należy jednak pamiętać, że Magazyn modeli nie jest bezpieczny dla wątków. Należy zawsze używać wątku interfejsu użytkownika, aby wprowadzać aktualizacje, a jeśli jest to możliwe, Zapobiegaj dokonywaniu edycji przez użytkownika, gdy operacja w tle jest w toku. Aby zapoznać się z przykładem, zobacz [aktualizowanie modelu UML z wątku w tle](../modeling/update-a-uml-model-from-a-background-thread.md).

## <a name="Executing"></a>Wykonywanie polecenia menu
 W celach testowych wykonaj polecenie w trybie debugowania.

#### <a name="to-test-the-menu-command"></a>Aby przetestować polecenie menu

1. Naciśnij klawisz **F5**lub w menu **Debuguj** wybierz polecenie **Rozpocznij debugowanie**.

     Zostanie uruchomione doświadczalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

     **Rozwiązywanie problemów**: jeśli nowy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie zostanie uruchomiony:

    - Jeśli masz więcej niż jeden projekt, upewnij się, że projekt VSIX jest ustawiony jako projekt startowy rozwiązania.

    - W Eksplorator rozwiązań, w menu skrótów dla uruchamiania lub tylko projektu, wybierz **Właściwości**. W edytorze właściwości projektu wybierz kartę **debugowanie** . Upewnij się, że ciąg w polu **początkowy program zewnętrzny** jest pełną ścieżką do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zazwyczaj:

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]eksperymentalnym Otwórz lub Utwórz projekt modelowania, a następnie otwórz lub Utwórz diagram modelowania. Użyj diagramu, który należy do jednego z typów wymienionych w atrybucie klasy poleceń menu.

3. Otwórz menu skrótów w dowolnym miejscu na diagramie. Polecenie powinno pojawić się w menu.

     **Rozwiązywanie problemów**: Jeśli polecenie nie pojawia się w menu, upewnij się, że:

    - Projekt polecenia menu jest wymieniony jako składnik MEF na karcie **zasoby** w pliku **source. Extensions. manifest** w projekcie VSIX.

    - Parametry `Import` i `Export` atrybuty są prawidłowe.

    - Metoda `QueryStatus` nie ustawia `command`.`Enabled` lub `Visible` pola do `false`.

    - Typ diagramu modelu, którego używasz (Klasa UML, sekwencja i tak dalej) jest wymieniony jako jeden z atrybutów klas poleceń menu `[ClassDesignerExtension]`, `[SequenceDesignerExtension]` i tak dalej.

## <a name="Installing"></a>Instalowanie i odinstalowywanie rozszerzenia
 Rozszerzenie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] można zainstalować zarówno na swoim komputerze, jak i na innych komputerach.

#### <a name="to-install-an-extension"></a>Aby zainstalować rozszerzenie

1. Na komputerze Znajdź plik **. vsix** , który został skompilowany przez projekt VSIX.

    1. W **Eksplorator rozwiązań**, w menu skrótów projektu VSIX, wybierz polecenie **Otwórz folder w Eksploratorze Windows**.

    2. Zlokalizuj plik **bin\\\*\\** _YourProject_ **. vsix**

2. Skopiuj plik **. vsix** do komputera docelowego, na którym chcesz zainstalować rozszerzenie. Może to być własny komputer lub inny.

     Komputer docelowy musi mieć jedną z wersji [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] określonych w elemencie **source. Extension. vsixmanifest**.

3. Na komputerze docelowym otwórz plik **. vsix** , na przykład klikając go dwukrotnie.

     Zostanie otwarty **Instalator rozszerzenia programu Visual Studio** , który zainstaluje rozszerzenie.

4. Uruchom lub Uruchom ponownie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Aby odinstalować rozszerzenie

1. W menu **Narzędzia** wybierz pozycję **rozszerzenia i aktualizacje**.

2. Rozwiń **zainstalowane rozszerzenia**.

3. Wybierz rozszerzenie, a następnie wybierz **Odinstaluj**.

   Rzadko błędne rozszerzenie nie zostanie załadowane i tworzy raport w oknie błędu, ale nie jest wyświetlany w Menedżerze rozszerzeń. W takim przypadku można usunąć rozszerzenie, usuwając plik z:

   *% LocalAppData%* **\Local\Microsoft\VisualStudio\\[wersja] \Extensions**

## <a name="MenuExample"></a>Przyklad
 Poniższy przykład pokazuje kod polecenia menu, które spowoduje wymianę nazw dwóch elementów na diagramie klas. Ten kod musi być skompilowany w projekcie rozszerzenia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i instalowany zgodnie z opisem w poprzednich sekcjach.

```
using System.Collections.Generic; // for IEnumerable
using System.ComponentModel.Composition;
  // for [Import], [Export]
using System.Linq; // for IEnumerable extensions
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
  // for IDiagramContext
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
  // for designer extension attributes
using Microsoft.VisualStudio.Modeling.Diagrams;
  // for ShapeElement
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
  // for IGestureExtension, ICommandExtension, ILinkedUndoContext
using Microsoft.VisualStudio.Uml.Classes;
  // for class diagrams, packages

/// <summary>
/// Extension to swap names of classes in a class diagram.
/// </summary>
namespace SwapClassNames
{
  // Declare the class as an MEF component:
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  // Add more ExportMetadata attributes to make
  // the command appear on diagrams of other types.
  public class NameSwapper : ICommandExtension
  {
  // MEF required interfaces:
  [Import]
  public IDiagramContext Context { get; set; }
  [Import]
  public ILinkedUndoContext LinkedUndoContext { get; set; }

  /// <summary>
  /// Swap the names of the currently selected elements.
  /// </summary>
  /// <param name="command"></param>
  public void Execute(IMenuCommand command)
  {
    // Get selected shapes that are IClassifiers -
    // IClasses, IInterfaces, IEnumerators.
    var selectedShapes = Context.CurrentDiagram
     .GetSelectedShapes<IClassifier>();
    if (selectedShapes.Count() < 2) return;

    // Get model elements displayed by shapes.
    IClassifier firstElement = selectedShapes.First().Element;
    IClassifier lastElement = selectedShapes.Last().Element;

    // Do the swap in a transaction so that user
    // cannot undo one change without the other.
    using (ILinkedUndoTransaction transaction =
    LinkedUndoContext.BeginTransaction("Swap names"))
    {
    string firstName = firstElement.Name;
    firstElement.Name = lastElement.Name;
    lastElement.Name = firstName;
    transaction.Commit();
    }
  }

  /// <summary>
  /// Called by Visual Studio to determine whether
  /// menu item should be visible and enabled.
  /// </summary>
  public void QueryStatus(IMenuCommand command)
  {
    int selectedClassifiers = Context.CurrentDiagram
     .GetSelectedShapes<IClassifier>().Count();
    command.Visible = selectedClassifiers > 0;
    command.Enabled = selectedClassifiers == 2;
  }

  /// <summary>
  /// Name of the menu command.
  /// </summary>
  public string Text
  {
    get { return "Swap Names"; }
  }
  }

}
```

## <a name="see-also"></a>Zobacz też
 [Definiowanie i Instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md) [Rozszerzanie modeli UML i diagramów](../modeling/extend-uml-models-and-diagrams.md) [Definiowanie obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md) [Definiowanie ograniczeń WALIDACJi dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md) [Edytowanie diagramów sekwencji UML przy użyciu programowania interfejsu API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md) UML z przykładowym [interfejsem API UML](../modeling/programming-with-the-uml-api.md) [: polecenie do wyrównywania kształtów na diagramie UML](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)
