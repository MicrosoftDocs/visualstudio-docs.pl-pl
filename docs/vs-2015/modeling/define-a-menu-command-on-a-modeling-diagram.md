---
title: Definiowanie polecenia menu na diagramie modelowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ef029cc6e931509997ad6f094adedc7d96e4bcd3
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670327"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>Definiowanie polecenia menu w diagramie modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można zdefiniować dodatkowe elementy menu w menu skrótów diagramu UML. Można kontrolować, czy polecenie menu pojawia się i jest włączone w menu skrótów każdego jakiegokolwiek elementu w diagramie i można napisać kod, który jest uruchamiany, gdy użytkownik wybierze element menu. Można spakować te rozszerzenia w rozszerzeniu integracji programu Visual Studio ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) i rozdystrybuować je innym użytkownikom programu Visual Studio.  

## <a name="requirements"></a>Wymagania  
 Zobacz [wymagania](../modeling/extend-uml-models-and-diagrams.md#Requirements).  

 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

## <a name="defining-the-menu-command"></a>Definiowanie polecenia menu  
 Aby utworzyć polecenie menu dla projektanta UML, należy utworzyć klasę, która definiuje zachowanie polecenia i osadzić tę klasę w Visual Studio Integration rozszerzenie (VSIX). VSIX działa jako kontener, który może zainstalować polecenia. Istnieją dwie alternatywne metody definiowania polecenia menu:  

-   **Utwórz polecenie menu w jego własnym VSIX przy użyciu szablonu projektu.** Jest to szybsza metoda. Użyj go, jeśli nie chcesz połączyć poleceń menu z innymi rodzajami rozszerzeń takich jak rozszerzenia sprawdzania poprawności, elementy do przybornika niestandardowego lub program obsługi gestów.  

-   **Utwórz osobne polecenie menu i projektów VSIX.** Użyj tej metody, jeśli chcesz połączyć kilka rodzajów rozszerzeń w samym VSIX. Na przykład jeśli polecenie menu oczekuje modelu do przestrzegania szczególnych ograniczeń, można ją osadzić w samym VSIX jako metodę sprawdzania poprawności.  

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>Aby utworzyć polecenie menu w jego własnym VSIX  

1. W **nowy projekt** dialogowego **projekty modelowania**, wybierz opcję **rozszerzenia polecenia**.  

2. Otwórz **.cs** plik w nowym projekcie i Modyfikuj `CommandExtension` klasę, aby wdrożyć swoje polecenie.  

    Aby uzyskać więcej informacji, zobacz [implementacja polecenia Menu](#Implementing).  

3. Dodatkowe polecenia można dodać do tego projektu, definiując nowe klasy.  

4. Przetestuj polecenie menu naciskając klawisz F5. Aby uzyskać więcej informacji, zobacz [wykonywanie polecenia Menu](#Executing).  

5. Zainstaluj polecenie menu na innym komputerze przez skopiowanie pliku **bin\\\*\\\*.vsix** utworzonego w projekcie. Aby uzyskać więcej informacji, zobacz [Instalowanie i odinstalowywanie rozszerzenia](#Installing).  

   W tym miejscu jest alternatywna procedura:  

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>Aby utworzyć polecenie menu w projekcie osobnej klasy biblioteki (DLL)  

1. Utwórz projekt biblioteki klas w nowym rozwiązaniu programu Visual Studio lub w istniejącym rozwiązaniu.  

   1.  Na **pliku** menu, wybierz **New**, **projektu**.  

   2.  W obszarze **zainstalowane szablony**, wybierz opcję **Visual C#** lub **języka Visual Basic**. W środkowej kolumnie Wybierz **biblioteki klas**.  

   3.  Ustaw **rozwiązania** do wskazania, czy chcesz, aby utworzyć nowe rozwiązanie lub dodać składnik do rozwiązania VSIX, które jest już otwarte.  

   4.  Ustaw projekt nazwę i lokalizację i kliknij przycisk OK.  

2. Dodaj następujące odwołania do projektu.  

   |                                                                                                    Tematy pomocy                                                                                                    |                                                                                                  Co to pozwala zrobić                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System.ComponentModel.Composition                                                                                        |                                         Zdefiniuj składniki za pomocą [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).                                          |
   |                                                                                      Microsoft.VisualStudio.Uml.Interfaces                                                                                      |                                                                                        Odczytaj i Zamień właściwości elementów modelu.                                                                                         |
   |                                                                             Microsoft.VisualStudio.ArchitectureTools.Extensibility                                                                              |                                                                                      Utwórz elementy modelu, Modyfikuj kształty na diagramach.                                                                                       |
   |                                                                                  Microsoft.VisualStudio.Modeling.Sdk.[version]                                                                                  | Zdefiniuj model obsługi zdarzeń.<br /><br /> Hermetyzuj serię zmian do modelu. Aby uzyskać więcej informacji, zobacz [aktualizacji modelu UML łącza za pomocą transakcji](../modeling/link-uml-model-updates-by-using-transactions.md). |
   |                                                            Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]<br /><br /> (nie zawsze wymagane)                                                             |                                                                                   Elementy diagramu dodatkowego dostępu dla procedur obsługi gestu.                                                                                   |
   | Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer<br /><br /> Wymagane tylko w przypadku polecenia na diagramach warstwy. Aby uzyskać więcej informacji, zobacz [rozszerzone diagramy warstw](../modeling/extend-layer-diagrams.md). |                                                                                             Zdefiniuj polecenia na diagramie warstwy.                                                                                              |

3. Dodaj plik klasy do projektu i ustawi jego zawartość do następującego kodu.  

   > [!NOTE]
   >  Zmień przestrzeń nazw, nazwę klasy i wartość zwracana przez `Text` zgodnie z preferencjami.  
   >   
   >  W przypadku zdefiniowania wielu poleceń, pojawiają się w menu w kolejności alfabetycznej według nazw klas.  

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

    Aby uzyskać więcej informacji o tym, co umieścić w metodach, zobacz [implementacja polecenia Menu](#Implementing).  

   Należy dodać polecenie menu do projektu VSIX, który działa jako kontener dla polecenia instalowania. Jeśli chcesz, możesz dodać inne składniki w tym samym VSIX.  

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>Aby dodać polecenie menu do projektu VSIX  

1.  Nie potrzebujesz tej procedury po utworzeniu polecenia menu z własnej VSIX.  

2.  Utwórz projekt VSIX, chyba że rozwiązanie zawiera już jeden.  

    1.  W **Eksploratora rozwiązań**, w menu skrótów rozwiązania wybierz **Dodaj**, **nowy projekt**.  

    2.  W obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C#** lub **języka Visual Basic**, następnie wybierz **rozszerzalności**. W środkowej kolumnie Wybierz **projekt VSIX**.  

3.  W Eksploratorze rozwiązań w menu skrótów projektu VSIX wybierz **Ustaw jako projekt startowy**.  

4.  Otwórz **source.extension.vsixmanifest**.  

    1.  Na **metadanych** kartę, ustaw nazwę VSIX.  

    2.  Na **Instaluj obiekty docelowe** kartę, należy ustawić wersji programu Visual Studio jako obiekty docelowe.  

    3.  Na **zasoby** kartę, wybrać **New**i w oknie dialogowym Ustaw:  

         **Typ** = **składnik MEF**  

         **Źródło** = **projekt w bieżącym rozwiązaniu**  

         **Projekt** = *projektu biblioteki klas*  

##  <a name="Implementing"></a> Implementowanie polecenia Menu  
 Klasa polecenia menu implementują metody wymagane dla <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>.  

|||  
|-|-|  
|`string Text { get; }`|Zwraca etykietę elementu menu.|  
|`void QueryStatus(IMenuCommand command);`|Wywołuje się, gdy użytkownik kliknie prawym przyciskiem myszy na diagramie.<br /><br /> Ta metoda nie powinna zmieniać modelu.<br /><br /> Użyj `DiagramContext.CurrentDiagram.SelectedShapes` ustalenie, czy polecenie są wyświetlane i można włączyć.<br /><br /> Zestaw:<br /><br /> -   `command.Visible` Aby `true` Jeśli polecenie musi znajdować się w menu po użytkownik kliknie prawym przyciskiem myszy na diagramie<br />-   `command.Enabled` Aby `true` Jeśli użytkownik może kliknąć polecenie w menu<br />-   `command.Text` Aby ustawić dynamicznie etykiety menu|  
|`void Execute (IMenuCommand command);`|Wywoływane, gdy użytkownik kliknie danego elementu menu, jeśli jest widoczne i włączone.|  

### <a name="accessing-the-model-in-code"></a>Uzyskiwanie dostępu do modelu w kodzie  
 Uwzględnianie następującej deklaracji w klasie polecenia menu:  

```  
[Import] public IDiagramContext DiagramContext { get; set; }  
```  

 ...  

 Deklaracja `IDiagramContext` umożliwia pisanie kodu w Twoich metodach, które uzyskuje dostęp do diagramu, bieżącego zaznaczenie i modelu:  

```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
{ IElement element = shape.Element; ... }  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}  
```  

### <a name="navigating-and-updating-the-model"></a>Nawigowanie i aktualizowanie modelu  
 Elementy modelu UML są dostępne za pośrednictwem interfejsu API. Z bieżącego zaznaczenia lub z katalogu głównego modelu są dostępne wszystkie inne elementy. Aby uzyskać więcej informacji, zobacz [nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md) i [Programowanie przy użyciu interfejsu API UML](../modeling/programming-with-the-uml-api.md).  

 Jeśli masz do czynienia z diagramem sekwencji, zobacz też [diagramy sekwencji UML edytować za pomocą interfejsu API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  

 Interfejs API umożliwia również zmienić właściwości elementów, usunięcie elementów i relacji i tworzenie nowych elementów i relacji.  

 Domyślnie każda zmiana wprowadzona w metodzie wykonaj będzie wykonywana w oddzielnej transakcji. Użytkownik będzie mógł cofnąć oddzielnie każdą zmianę. Jeśli chcesz grupować zmiany w pojedynczą transakcję, użyj <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> zgodnie z opisem w [aktualizacji modelu UML łącza za pomocą transakcji](../modeling/link-uml-model-updates-by-using-transactions.md).  

### <a name="use-the-ui-thread-for-updates"></a>Użycie wątku interfejsu użytkownika dla aktualizacji  
 W niektórych przypadkach może być przydatne do wykonywania aktualizacji do modelu z wątku w tle. Na przykład jeśli polecenia powoduje załadowanie danych z zasobów powolnych, można wykonać ładowanie w wątku tła tak, aby użytkownik może wyświetlić zmiany, gdy są w toku i anulować operację, jeśli to konieczne.  

 Jednak należy pamiętać, że magazyn modelu nie jest bezpieczny dla wątków. Należy zawsze Użyj wątku interfejsu użytkownika, aby wprowadzić aktualizacje i jeśli to możliwe, uniemożliwia użytkownikowi wprowadzanie zmian w trakcie operacji w tle. Aby uzyskać przykład, zobacz [aktualizowanie modelu UML z wątku w tle](../modeling/update-a-uml-model-from-a-background-thread.md).  

##  <a name="Executing"></a> Wykonywanie polecenia Menu  
 Do celów testowych wykonaj polecenia w trybie debugowania.  

#### <a name="to-test-the-menu-command"></a>Aby przetestować polecenia menu  

1.  Naciśnij klawisz **F5**, lub na **debugowania** menu, wybierz **Rozpocznij debugowanie**.  

     Eksperymentalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoczyna się.  

     **Rozwiązywanie problemów z**: Jeśli nowy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie można uruchomić:  

    -   Jeśli masz więcej niż jeden projekt, upewnij się, że projekt VSIX jest ustawiony jako projekt startowy rozwiązania.  

    -   W Eksploratorze rozwiązań w menu skrótów uruchamiania lub tylko projektu, wybierz **właściwości**. W edytorze właściwości projektu zaznacz **debugowania** kartę. Upewnij się, że ciąg w **uruchomienia programu zewnętrznego** pole jest pełna nazwa ścieżki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zazwyczaj:  

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  

2.  W eksperymentalnym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Otwórz lub Utwórz projekt modelowania i otworzyć lub utworzyć diagram modelowania. Użyj diagramu, który należy do jednego z typów wymienionych w atrybucie klasy polecenia menu.  

3.  Otwórz menu skrótów w dowolnym miejscu na diagramie. Twoje polecenie powinno pojawić się w menu.  

     **Rozwiązywanie problemów z**: Jeśli nie ma polecenia menu, upewnij się, że:  

    -   Projekt polecenia menu jest wymieniony jako składnik listy MEF **zasoby** karcie **source.extensions.manifest** w projekcie VSIX.  

    -   Parametry `Import` i `Export` atrybuty są prawidłowe.  

    -   `QueryStatus` Metoda nie ustawia `command`.`Enabled` lub `Visible` polom `false`.  

    -   Typ diagramu modelu, że używasz (UML klasy, sekwencja i tak dalej) jest wymieniony jako jeden z atrybutów klasy polecenia menu `[ClassDesignerExtension]`, `[SequenceDesignerExtension]` i tak dalej.  

##  <a name="Installing"></a> Instalowanie i odinstalowywanie rozszerzenia  
 Możesz zainstalować [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozszerzenie zarówno na swoim komputerze, jak i na innych komputerach.  

#### <a name="to-install-an-extension"></a>Aby zainstalować rozszerzenie  

1.  Na komputerze, należy znaleźć **.vsix** pliku, który został zbudowany w danym projekcie VSIX.  

    1.  W **Eksploratora rozwiązań**, w menu skrótów projektu VSIX wybierz **Otwórz Folder w Eksploratorze Windows**.  

    2.  Zlokalizuj plik **bin\\\*\\**_YourProject_**.vsix**  

2.  Kopiuj **.vsix** plik na komputer docelowy, na którym chcesz zainstalować rozszerzenie. Może to być Twój własny komputer lub innej.  

     Komputer docelowy musi mieć jedną z wersji [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ustawionego w **source.extension.vsixmanifest**.  

3.  Na komputerze docelowym, otwórz **.vsix** pliku, na przykład, klikając go dwukrotnie.  

     **Instalator rozszerzenia programu Visual Studio** otwiera i instaluje rozszerzenia.  

4.  Uruchom lub uruchom ponownie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  

#### <a name="to-uninstall-an-extension"></a>Aby odinstalować rozszerzenie  

1. Na **narzędzia** menu, wybierz **rozszerzenia i aktualizacje**.  

2. Rozwiń **zainstalowanych rozszerzeń**.  

3. Zaznacz rozszerzenie, a następnie wybierz **Odinstaluj**.  

   Rzadko wadliwe rozszerzenie nie ładuje się i tworzy raport w oknie błędów, ale nie są wyświetlane w Menedżerze rozszerzeń. W takim przypadku należy usunąć rozszerzenie przez usunięcie pliku:  

   *% LocalAppData %* **\Local\Microsoft\VisualStudio\\\Extensions [wersja]**  

##  <a name="MenuExample"></a> Przykład  
 Poniższy przykład pokazuje kod dla polecenia menu, które zamieni nazwy dwóch elementów na diagramie klasy. Ten kod musi być zbudowany w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenie projektu i zainstalowany zgodnie z opisem w poprzedniej sekcji.  

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
 [Definiowanie i instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md)   
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definiowanie procedury obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Edytowanie diagramów sekwencji UML przy użyciu interfejsu API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)   
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)   
 [Przykład: Polecenie połączenia kształtów w diagramie UML](http://go.microsoft.com/fwlink/?LinkID=213809)
