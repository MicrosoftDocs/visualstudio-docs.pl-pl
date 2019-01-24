---
title: Definiowanie procedury obsługi gestów na diagramie modelowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ecd6f6210fdc219f7d1ca493f15beed74e9b5e2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54778849"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>Definiowanie procedury obsługi gestów na diagramie modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można zdefiniować polecenia, które są wykonywane, gdy użytkownik kliknie dwukrotnie lub przeciąganie elementy na UML diagram. Można spakować te rozszerzenia w rozszerzeniu integracji programu Visual Studio ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) i rozdystrybuować je innym użytkownikom programu Visual Studio.  
  
 Jeśli istnieje już wbudowane zachowanie dla typu diagramu i typu elementu, który chcesz przeciągnąć, nie można dodać lub zmienić to zachowanie.  
  
## <a name="requirements"></a>Wymagania  
 Zobacz [wymagania](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="creating-a-gesture-handler"></a>Tworzenie procedury obsługi gestu  
 Aby zdefiniować procedury obsługi gestu dla projektanta UML, należy utworzyć klasę, która definiuje zachowanie obsługi gestu i osadzić tę klasę w Visual Studio Integration rozszerzenie (VSIX). VSIX działa jako kontener, który może zainstalować obsługę. Istnieją dwie alternatywne metody definiowania obsługi gestu:  
  
-   **Utwórz procedurę obsługi gestu w jego własnym VSIX przy użyciu szablonu projektu.** Jest to szybsza metoda. Użyj go, jeśli nie chcesz połączyć programu obsługi z innymi rodzajami rozszerzeń takich jak rozszerzenia sprawdzania poprawności, elementy do przybornika niestandardowego lub polecenia menu.  
  
-   **Utwórz osobną procedurę obsługi gestu i projektów VSIX.** Użyj tej metody, jeśli chcesz połączyć kilka rodzajów rozszerzeń w samym VSIX. Na przykład jeśli procedura obsługi gestu oczekuje modelu do przestrzegania szczególnych ograniczeń, można ją osadzić w samym VSIX jako metodę sprawdzania poprawności.  
  
#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>Aby utworzyć obsługę gestu w jego własnym VSIX  
  
1. W **nowy projekt** dialogowego **projekty modelowania**, wybierz opcję **rozszerzenia gestu**.  
  
2. Otwórz **.cs** plik w nowym projekcie i Modyfikuj `GestureExtension` klasę, aby wdrożyć swój plik obsługi gestów.  
  
    Aby uzyskać więcej informacji, zobacz [Implementowanie obsługi gest](#Implementing).  
  
3. Przetestuj obsługę gestu naciskając klawisz F5. Aby uzyskać więcej informacji, zobacz [wykonywanie obsługi gestu](#Executing).  
  
4. Instalowanie obsługi gestu na innym komputerze przez skopiowanie pliku **bin\\\*\\\*.vsix** utworzonego w projekcie. Aby uzyskać więcej informacji, zobacz [Instalowanie i odinstalowywanie rozszerzenia](#Installing).  
  
   W tym miejscu jest alternatywna procedura:  
  
#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>Aby utworzyć projekt osobnej klasy biblioteki (DLL) dla obsługi gestu  
  
1. Utwórz projekt biblioteki klas w nowym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania, lub w istniejącym rozwiązaniu.  
  
   1.  Na **pliku** menu, wybierz **New**, **projektu**.  
  
   2.  W obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C#** lub **języka Visual Basic**, następnie w środkowej kolumnie Wybierz **biblioteki klas**.  
  
2. Dodaj następujące odwołania do projektu.  
  
    `Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`  
  
    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`  
  
    `Microsoft.VisualStudio.Uml.Interfaces`  
  
    `System.ComponentModel.Composition`  
  
    `System.Windows.Forms`  
  
    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` — Jest to potrzebne tylko w przypadku rozszerzenia diagramów warstwy. Aby uzyskać więcej informacji, zobacz [rozszerzone diagramy warstw](../modeling/extend-layer-diagrams.md).  
  
3. Dodaj plik klasy do projektu i ustawi jego zawartość do następującego kodu.  
  
   > [!NOTE]
   >  Zmień nazwę przestrzeni nazw i klasy, zgodnie z preferencjami.  
  
   ```  
   using System.ComponentModel.Composition;  
   using System.Linq;  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Modeling.Diagrams;  
   using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
   using Microsoft.VisualStudio.Modeling;  
   using Microsoft.VisualStudio.Uml.Classes;  
   // ADD other UML namespaces if required  
  
   namespace MyGestureHandler // CHANGE  
   {  
     // DELETE any of these attributes if the handler  
     // should not work with some types of diagram.  
     [ClassDesignerExtension]  
     [ActivityDesignerExtension]  
     [ComponentDesignerExtension]  
     [SequenceDesignerExtension]  
     [UseCaseDesignerExtension]  
     // [LayerDesignerExtension]  
  
     // Gesture handlers must export IGestureExtension:  
     [Export(typeof(IGestureExtension))]  
     // CHANGE class name  
     public class MyGesture1 : IGestureExtension  
     {  
       [Import]  
       public IDiagramContext DiagramContext { get; set; }  
  
       /// <summary>  
       /// Called when the user double-clicks on the diagram  
       /// </summary>  
       /// <param name="targetElement"></param>  
       /// <param name="diagramPointEventArgs"></param>  
       public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)  
       {  
         // CHANGE THIS CODE FOR YOUR APPLICATION.  
  
         // Get the target shape, if any. Null if the target is the diagram.  
         IShape targetIShape = targetElement.CreateIShape();  
  
         // Do something...  
       }  
  
       /// <summary>  
       /// Called repeatedly when the user drags from anywhere on the screen.  
       /// Return value should indicate whether a drop here is allowed.  
       /// </summary>  
       /// <param name="targetMergeElement">References the element to be dropped on.</param>  
       /// <param name="diagramDragEventArgs">References the element to be dropped.</param>  
       /// <returns></returns>  
       public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)  
       {  
         // CHANGE THIS CODE FOR YOUR APPLICATION.  
  
         // Get the target element, if any. Null if the target is the diagram.  
         IShape targetIShape = targetMergeElement.CreateIShape();  
  
         // This example allows drag of any UML elements.  
         return GetModelElementsFromDragEvent(diagramDragEventArgs).Count() > 0;  
       }  
  
       /// <summary>  
       /// Execute the action to be performed on the drop.  
       /// </summary>  
       /// <param name="targetDropElement"></param>  
       /// <param name="diagramDragEventArgs"></param>  
       public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
       {  
         // CHANGE THIS CODE FOR YOUR APPLICATION.  
       }  
  
       /// <summary>  
       /// Retrieves UML IElements from drag arguments.  
       /// Works for drags from UML diagrams.  
       /// </summary>  
       private IEnumerable<IElement> GetModelElementsFromDragEvent  
               (DiagramDragEventArgs dragEvent)  
       {  
         //ElementGroupPrototype is the container for  
         //dragged and copied elements and toolbox items.  
         ElementGroupPrototype prototype =  
            dragEvent.Data.  
            GetData(typeof(ElementGroupPrototype))  
                 as ElementGroupPrototype;  
         // Locate the originals in the implementation store.  
         IElementDirectory implementationDirectory =  
            dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;  
  
         return prototype.ProtoElements.Select(  
           prototypeElement =>  
           {  
             ModelElement element = implementationDirectory  
               .FindElement(prototypeElement.ElementId);  
             ShapeElement shapeElement = element as ShapeElement;  
             if (shapeElement != null)  
             {  
               // Dragged from a diagram.  
               return shapeElement.ModelElement as IElement;  
             }  
             else  
             {  
               // Dragged from UML Model Explorer.  
               return element as IElement;  
             }  
           });  
       }  
  
     }  
   }  
  
   ```  
  
    Aby uzyskać więcej informacji o tym, co umieścić w metodach, zobacz [Implementowanie obsługi gest](#Implementing).  
  
   Należy dodać polecenie menu do projektu VSIX, który działa jako kontener dla polecenia instalowania. Jeśli chcesz, możesz dodać inne składniki w tym samym VSIX.  
  
#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>Aby dodać oddzielnych gestów do projektu VSIX  
  
1.  Nie trzeba tej procedury, jeśli użytkownik utworzył procedurę obsługi gestu z własnej VSIX.  
  
2.  Utwórz projekt VSIX, chyba że rozwiązanie zawiera już jeden.  
  
    1.  W **Eksploratora rozwiązań**, w menu skrótów rozwiązania wybierz **Dodaj**, **nowy projekt**.  
  
    2.  W obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C#** lub **języka Visual Basic**, a następnie wybierz **rozszerzalności**. W środkowej kolumnie Wybierz **projekt VSIX**.  
  
3.  Ustaw projekt VSIX jako projekt startowy rozwiązania.  
  
    -   W Eksploratorze rozwiązań w menu skrótów projektu VSIX wybierz **Ustaw jako projekt startowy**.  
  
4.  W **source.extension.vsixmanifest**, Dodaj projekt biblioteki klas obsługi gest jako składnik MEF:  
  
    1.  Na **metadanych** kartę, ustaw nazwę VSIX.  
  
    2.  Na **Instaluj obiekty docelowe** kartę, należy ustawić wersji programu Visual Studio jako obiekty docelowe.  
  
    3.  Na **zasoby** kartę, wybrać **New**i w oknie dialogowym Ustaw:  
  
         **Typ** = **składnik MEF**  
  
         **Źródło** = **projekt w bieżącym rozwiązaniu**  
  
         **Projekt** = *projektu biblioteki klas*  
  
##  <a name="Executing"></a> Wykonywanie obsługi gestu  
 Do celów testowych wykonaj procedurę obsługi gestu w trybie debugowania.  
  
#### <a name="to-test-the-gesture-handler"></a>Testowanie obsługi gestu  
  
1. Naciśnij klawisz **F5**, lub na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
    Eksperymentalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoczyna się.  
  
    **Rozwiązywanie problemów z**: Jeśli nowy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie można uruchomić:  
  
   -   Jeśli masz więcej niż jeden projekt, upewnij się, że projekt VSIX jest ustawiony jako projekt startowy rozwiązania.  
  
   -   W Eksploratorze rozwiązań w menu skrótów uruchamiania lub tylko projektu, wybierz polecenie Właściwości. W edytorze właściwości projektu, wybierz **debugowania** kartę. Upewnij się, że ciąg w **uruchomienia programu zewnętrznego** pole jest pełna nazwa ścieżki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zazwyczaj:  
  
        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  
  
2. W eksperymentalnym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Otwórz lub Utwórz projekt modelowania i otworzyć lub utworzyć diagram modelowania. Użyj diagramu, który należy do jednego z typów wymienionych w atrybucie klasy programu obsługi gestu.  
  
3. Kliknij dwukrotnie dowolne miejsce na diagramie. Program obsługi dwukrotnego kliknięcia powinien zostać wywołany.  
  
4. Przeciągnij element z Eksploratora UML na diagram. Program obsługi przeciągnięcia powinien zostać wywołany.  
  
   **Rozwiązywanie problemów z**: Jeśli program obsługi gestu nie działa, upewnij się, że:  
  
-   Projekt obsługi gestu jest wymieniony jako składnik listy MEF **zasoby** karcie **source.extensions.manifest** w projekcie VSIX.  
  
-   Parametry wszystkich `Import` i `Export` atrybuty są prawidłowe.  
  
-   `CanDragDrop` Metoda nie zwraca `false`.  
  
-   Typ modelu diagram, którego używasz (UML klasy, sekwencja i tak dalej) jest wymieniony jako jeden z gestów obsługi atrybutów klasy polecenia [ClassDesignerExtension], [SequenceDesignerExtension] i tak dalej.  
  
-   Nie ma żadnych funkcji wbudowanych już zdefiniowanych dla tego typu docelowego i elementu porzuconego.  
  
##  <a name="Implementing"></a> Wdrażanie obsługi gestu  
  
### <a name="the-gesture-handler-methods"></a>Metody obsługi gestu  
 Klasy obsługi gestu implementuje i eksportuje <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>. Metody, które należy zdefiniować, są następujące:  
  
|||  
|-|-|  
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Zwróć `true` Aby zezwolić elementowi źródła wymienionemu w `dragEvent` do porzucony w tym elemencie docelowym.<br /><br /> Ta metoda nie powinna dokonywać zmian w modelu. Powinna działać szybko, ponieważ jest używany do określania stanu strzałki gdy użytkownik przesuwa mysz.|  
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Zaktualizuj model oparty na obiekcie źródłowym, do którego odwołuje się `dragEvent`, jak i obiektem docelowym.<br /><br /> Wywołuje się, gdy użytkownik zwolni przycisk myszy po przeciągnięciu.|  
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` jest kształtem, który zostanie kliknięty dwukrotnie.|  
  
 Można napisać procedury obsługi, które mogą również akceptować UML, nie tylko cały szereg innych elementów, takich jak pliki, węzły w widoku klasy .NET i tak dalej. Użytkownik można przeciągnąć te elementy na diagramie UML warunkiem, że zapiszesz `OnDragDrop` metodę, która mogą dekodować serializowane postaci elementów. Metody dekodowania różnią się od jeden typ elementu do innego.  
  
 Parametry tych metod są:  
  
-   `ShapeElement target`. Kształt lub diagram, na którym użytkownik przenosi coś.  
  
     `ShapeElement` jest klasą we wdrażaniu, która jest podporządkowana narzędziu UML narzędzia do modelowania. Aby zmniejszyć ryzyko wprowadzenia modelu UML i diagramów w niespójnym stanie, firma Microsoft zaleca, aby używać metody tej klasy bezpośrednio. Zamiast tego, owiń element w `IShape`, a następnie użyj metod opisanych w [wyświetlanie modelu UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md).  
  
    -   Aby uzyskać `IShape`:  
  
        ```  
        IShape targetIShape = target.CreateIShape(target);  
        ```  
  
    -   Aby uzyskać element modelu, który jest określony przez przeciąganie lub operację dwukrotnego kliknięcia:  
  
        ```  
        IElement target = targetIShape.Element;  
        ```  
  
         Można rzutować to do bardziej określonego typu elementu.  
  
    -   Aby uzyskać magazyn modeli UML, który zawiera UML model:  
  
        ```  
        IModelStore modelStore =   
          targetIShape.Element.GetModelStore();   
        ```  
  
    -   Aby uzyskać dostęp do hosta i usługodawcy:  
  
        ```  
        target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE  
        ```  
  
-   `DiagramDragEventArgs eventArgs`. Ten parametr niesie ze sobą serializowany formularz z obiektem źródłowym operacji przeciągania:  
  
    ```  
    System.Windows.Forms.IDataObject data = eventArgs.Data;    
    ```  
  
     Można przeciągnąć elementy różnego rodzaju na diagramie z różnych części [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], lub z pulpitu Windows. Różne rodzaje elementu są zakodowane w różny sposób w `IDataObject`. Aby wyodrębnić elementy z niego, zajrzyj do dokumentacji dla odpowiedniego typu obiektu.  
  
     Jeśli obiekt źródłowy jest elementem UML przeciągniętym z Eksploratora modelu UML lub innego diagramu UML, zobacz [elementów modelu UML Pobierz z elementu IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).  
  
### <a name="writing-the-code-of-the-methods"></a>Pisanie kodu metody  
 Aby uzyskać więcej informacji na temat pisania kodu do odczytu i aktualizacji modelu, zobacz [Programowanie przy użyciu interfejsu API UML](../modeling/programming-with-the-uml-api.md).  
  
 Aby uzyskać informacji na temat uzyskiwania dostępu do informacji o modelu w operacji przeciągania, zobacz [elementów modelu UML Pobierz z elementu IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).  
  
 Jeśli masz do czynienia z diagramem sekwencji, zobacz też [diagramy sekwencji UML edytować za pomocą interfejsu API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
 Oprócz parametrów metody można również zadeklarować importowane właściwości w swojej klasie, która zapewnia dostęp do bieżącego diagramu i modelu.  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
```  
  
 Deklaracja `IDiagramContext` umożliwia pisanie kodu w Twoich metodach, które uzyskuje dostęp do diagramu, bieżącego zaznaczenie i modelu:  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)  
{ IElement element = shape.Element; ... }  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IDiagram diagram in modelStore.Diagrams) {...}  
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}  
```  
  
 Aby uzyskać więcej informacji, zobacz [nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md).  
  
##  <a name="Installing"></a> Instalowanie i odinstalowywanie rozszerzenia  
 Możesz zainstalować [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozszerzenie zarówno na swoim komputerze, jak i na innych komputerach.  
  
#### <a name="to-install-an-extension"></a>Aby zainstalować rozszerzenie  
  
1.  Na komputerze, należy znaleźć **.vsix** pliku, który został zbudowany w danym projekcie VSIX.  
  
    1.  W **Eksploratora rozwiązań**, w menu skrótów projektu VSIX wybierz **Otwórz Folder w Eksploratorze Windows**.  
  
    2.  Zlokalizuj plik **bin\\\*\\**_YourProject_**.vsix**  
  
2.  Kopiuj **.vsix** plik na komputer docelowy, na którym chcesz zainstalować rozszerzenie. Może to być Twój własny komputer lub innej.  
  
     Komputer docelowy musi mieć jedną z wersji [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ustawionego w **source.extension.vsixmanifest**.  
  
3.  Na komputerze docelowym, otwórz **.vsix** pliku.  
  
     **Instalator rozszerzenia programu Visual Studio** otwiera i instaluje rozszerzenia.  
  
4.  Uruchom lub uruchom ponownie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-uninstall-an-extension"></a>Aby odinstalować rozszerzenie  
  
1. Na **narzędzia** menu, wybierz **rozszerzenia i aktualizacje**.  
  
2. Rozwiń **zainstalowanych rozszerzeń**.  
  
3. Zaznacz rozszerzenie, a następnie wybierz **Odinstaluj**.  
  
   Rzadko wadliwe rozszerzenie nie ładuje się i tworzy raport w oknie błędów, ale nie są wyświetlane w Menedżerze rozszerzeń. W takim przypadku należy usunąć rozszerzenie przez usunięcie pliku:  
  
   *% LocalAppData %* **\Local\Microsoft\VisualStudio\\\Extensions [wersja]**  
  
##  <a name="DragExample"></a> Przykład  
 Poniższy przykład pokazuje sposób tworzenia linii życia w diagramie sekwencji na podstawie części i portów składnika przeciągniętych z diagramu składników.  
  
 Aby przetestować go, naciśnij klawisz F5. Otwiera doświadczalne wystąpienie programu Visual Studio. W tym wypadku Otwórz UML model i Utwórz składnik na diagramie składników. Dodaj do tego składnika niektóre interfejsy i wewnętrzne części zamienne. Wybierz interfejsy i części. Następnie przeciągnij interfejsy i części na diagramie sekwencji. (Przeciągnij z diagramu składników w górę do karty diagramu sekwencji, a następnie w dół do diagramu sekwencji.) Linia życia pojawi się dla poszczególnych interfejsów i części.  
  
 Aby uzyskać więcej informacji o wiązaniu interakcji do diagramów sekwencji, zobacz [diagramy sekwencji UML edytować za pomocą interfejsu API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
```  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.Uml.Interactions;  
using Microsoft.VisualStudio.Uml.CompositeStructures;  
using Microsoft.VisualStudio.Uml.Components;  
  
/// <summary>  
/// Creates lifelines from component ports and parts.  
/// </summary>  
[Export(typeof(IGestureExtension))]  
[SequenceDesignerExtension]  
public class CreateLifelinesFromComponentParts : IGestureExtension  
{  
  [Import]  
  public IDiagramContext Context { get; set; }  
  
  /// <summary>  
  /// Called by the modeling framework when  
  /// the user drops something on a target.  
  /// </summary>  
  /// <param name="target">The target shape or diagram </param>  
  /// <param name="dragEvent">The item being dragged</param>  
  public void OnDragDrop(ShapeElement target,  
           DiagramDragEventArgs dragEvent)  
  {  
    ISequenceDiagram diagram = Context.CurrentDiagram  
            as ISequenceDiagram;  
    IInteraction interaction = diagram.Interaction;  
    if (interaction == null)  
    {  
      // Sequence diagram is empty: create an interaction.  
      interaction = diagram.ModelStore.Root.CreateInteraction();  
      interaction.Name = Context.CurrentDiagram.Name;  
      diagram.Bind(interaction);  
    }  
    foreach (IConnectableElement connectable in  
       GetConnectablesFromDrag(dragEvent))  
    {  
      ILifeline lifeline = interaction.CreateLifeline();  
      lifeline.Represents = connectable;  
      lifeline.Name = connectable.Name;  
    }  
  }  
  
  /// <summary>  
  /// Called by the modeling framework to determine whether  
  /// the user can drop something on a target.  
  /// Must not change anything.  
  /// </summary>  
  /// <param name="target">The target shape or diagram</param>  
  /// <param name="dragEvent">The item being dragged</param>  
  /// <returns>true if this item can be dropped on this target</returns>  
  public bool CanDragDrop(ShapeElement target,  
           DiagramDragEventArgs dragEvent)  
  {  
    IEnumerable<IConnectableElement> connectables = GetConnectablesFromDrag(dragEvent);  
    return connectables.Count() > 0;  
  }  
  
  ///<summary>  
  /// Get dragged parts and ports of an IComponent.  
  ///</summary>  
  private IEnumerable<IConnectableElement>  
    GetConnectablesFromDrag(DiagramDragEventArgs dragEvent)  
  {  
    foreach (IElement element in  
      GetModelElementsFromDragEvent(dragEvent))  
    {  
      IConnectableElement part = element as IConnectableElement;  
      if (part != null)  
      {  
        yield return part;  
      }  
    }  
  }  
  
  /// <summary>  
  /// Retrieves UML IElements from drag arguments.  
  /// Works for drags from UML diagrams.  
  /// </summary>  
  private IEnumerable<IElement> GetModelElementsFromDragEvent  
          (DiagramDragEventArgs dragEvent)  
  {  
    //ElementGroupPrototype is the container for  
    //dragged and copied elements and toolbox items.  
    ElementGroupPrototype prototype =  
       dragEvent.Data.  
       GetData(typeof(ElementGroupPrototype))  
            as ElementGroupPrototype;  
    // Locate the originals in the implementation store.  
    IElementDirectory implementationDirectory =  
       dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;  
  
    return prototype.ProtoElements.Select(  
      prototypeElement =>  
      {  
        ModelElement element = implementationDirectory  
          .FindElement(prototypeElement.ElementId);  
        ShapeElement shapeElement = element as ShapeElement;  
        if (shapeElement != null)  
        {  
          // Dragged from a diagram.  
          return shapeElement.ModelElement as IElement;  
        }  
        else  
        {  
          // Dragged from UML Model Explorer.  
          return element as IElement;  
        }  
      });  
  }  
  
  public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)  
  {  
  }  
}  
  
```  
  
 Kod `GetModelElementsFromDragEvent()` jest opisana w [elementów modelu UML Pobierz z elementu IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie i instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md)   
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)
