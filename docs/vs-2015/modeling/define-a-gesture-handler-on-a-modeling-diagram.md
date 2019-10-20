---
title: Definiowanie obsługi gestów na diagramie modelowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fbf111dbf8297994994f10b9b867e03321268679
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654872"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>Definiowanie procedury obsługi gestów na diagramie modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można definiować polecenia, które są wykonywane, gdy użytkownik kliknie dwukrotnie lub przeciągnie elementy na diagram UML. Można spakować te rozszerzenia w rozszerzeniu integracji programu Visual Studio ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) i przekazać je do innych użytkowników programu Visual Studio.

 Jeśli istnieje już wbudowane zachowanie dla typu diagramu i typu elementu, który chcesz przeciągnąć, możesz nie być w stanie dodać lub zastąpić to zachowanie.

## <a name="requirements"></a>Wymagania
 Zobacz [wymagania](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-gesture-handler"></a>Tworzenie procedury obsługi gestu
 Aby zdefiniować procedurę obsługi gestu dla projektanta UML, należy utworzyć klasę, która definiuje zachowanie obsługi gestu i osadzić tę klasę w rozszerzeniu integracji programu Visual Studio (VSIX). VSIX działa jako kontener, który może zainstalować procedurę obsługi. Istnieją dwie alternatywne metody definiowania procedury obsługi gestu:

- **Utwórz procedurę obsługi gestu w jego własnym VSIX przy użyciu szablonu projektu.** To jest szybka metoda. Użyj go, jeśli nie chcesz łączyć programu obsługi z innymi typami rozszerzeń, takimi jak rozszerzenia walidacji, niestandardowe elementy przybornika lub polecenia menu.

- **Utwórz osobną procedurę obsługi gestu i projekty VSIX.** Użyj tej metody, jeśli chcesz połączyć kilka typów rozszerzeń z tym samym VSIX. Na przykład, jeśli program obsługi gestu oczekuje modelu do przestrzegania określonych ograniczeń, można go osadzić w tym samym VSIX jako metodę sprawdzania poprawności.

#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>Aby utworzyć procedurę obsługi gestu w jego własnym VSIX

1. W oknie dialogowym **Nowy projekt** w obszarze **projekty modelowania**wybierz pozycję **rozszerzenie gestu**.

2. Otwórz plik **CS** w nowym projekcie i zmodyfikuj klasę `GestureExtension`, aby zaimplementować obsługę gestu.

    Aby uzyskać więcej informacji, zobacz [implementowanie obsługi gestu](#Implementing).

3. Przetestuj procedurę obsługi gestu, naciskając klawisz F5. Aby uzyskać więcej informacji, zobacz [wykonywanie procedury obsługi gestu](#Executing).

4. Zainstaluj procedurę obsługi gestu na innym komputerze przez skopiowanie pliku **bin \\ \* \\ \*. vsix** skompilowanego przez projekt. Aby uzyskać więcej informacji, zobacz [Instalowanie i odinstalowywanie rozszerzenia](#Installing).

   Oto alternatywna procedura:

#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>Aby utworzyć oddzielny projekt biblioteki klas (DLL) dla programu obsługi gestu

1. Utwórz projekt biblioteki klas w nowym rozwiązaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub w istniejącym rozwiązaniu.

   1. W menu **plik** wybierz polecenie **Nowy**, **projekt**.

   2. W obszarze **zainstalowane szablony**rozwiń **pozycję C# Wizualizacja** lub **Visual Basic**, a następnie w środkowej kolumnie Wybierz pozycję **Biblioteka klas**.

2. Dodaj następujące odwołania do projektu.

    `Microsoft.VisualStudio.Modeling.Sdk.[version]`

    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`

    `Microsoft.VisualStudio.Uml.Interfaces`

    `System.ComponentModel.Composition`

    `System.Windows.Forms`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` — jest to konieczne tylko wtedy, gdy rozszerzasz diagramy warstwowe. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając diagramy warstwowe](../modeling/extend-layer-diagrams.md).

3. Dodaj plik klasy do projektu i ustaw jego zawartość na następujący kod.

   > [!NOTE]
   > Zmień przestrzeń nazw i nazwę klasy zgodnie z preferencjami.

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

    Aby uzyskać więcej informacji o tym, co należy umieścić w metodach, zobacz [implementowanie obsługi gestu](#Implementing).

   Należy dodać polecenie menu do projektu VSIX, który działa jako kontener służący do instalowania polecenia. Jeśli chcesz, możesz dołączyć inne składniki do tego samego VSIX.

#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>Aby dodać osobną procedurę obsługi gestu do projektu VSIX

1. Ta procedura nie jest potrzebna, jeśli utworzono procedurę obsługi gestu przy użyciu własnego VSIX.

2. Utwórz projekt VSIX, chyba że rozwiązanie już go posiada.

    1. W **Eksplorator rozwiązań**, w menu skrótów rozwiązania, wybierz **Dodaj**, **Nowy projekt**.

    2. W obszarze **zainstalowane szablony**rozwiń **pozycję C# Wizualizacja** lub **Visual Basic**, a następnie wybierz pozycję **rozszerzalność**. W środkowej kolumnie Wybierz pozycję **Projekt VSIX**.

3. Ustaw projekt VSIX jako projekt startowy rozwiązania.

    - W Eksplorator rozwiązań, w menu skrótów projektu VSIX, wybierz **Ustaw jako projekt startowy**.

4. W elemencie **source. Extension. vsixmanifest**Dodaj projekt biblioteki klas obsługi gestów jako składnik MEF:

    1. Na karcie **metadane** Ustaw nazwę VSIX.

    2. Na karcie **Instalowanie obiektów docelowych** Ustaw wersje programu Visual Studio jako elementy docelowe.

    3. Na karcie **zasoby** wybierz pozycję **Nowy**, a następnie w oknie dialogowym Ustaw wartość:

         **Typ**  = **składnik MEF**

         **Źródło**  = **projektu w bieżącym rozwiązaniu**

         **Projekt**  = *projektu biblioteki klas*

## <a name="Executing"></a>Wykonywanie procedury obsługi gestu
 W celach testowych wykonaj procedurę obsługi gestu w trybie debugowania.

#### <a name="to-test-the-gesture-handler"></a>Aby przetestować procedurę obsługi gestu

1. Naciśnij klawisz **F5**lub w menu **debugowanie** kliknij **Rozpocznij debugowanie**.

    Zostanie uruchomione doświadczalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

    **Rozwiązywanie problemów**: jeśli nowy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie zostanie uruchomiony:

   - Jeśli masz więcej niż jeden projekt, upewnij się, że projekt VSIX jest ustawiony jako projekt startowy rozwiązania.

   - W Eksplorator rozwiązań, w menu skrótów dla uruchamiania lub tylko projektu, wybierz właściwości. W edytorze właściwości projektu wybierz kartę **debugowanie** . Upewnij się, że ciąg w polu **początkowy program zewnętrzny** jest pełną ścieżką do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zazwyczaj:

        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eksperymentalnym Otwórz lub Utwórz projekt modelowania, a następnie otwórz lub Utwórz diagram modelowania. Użyj diagramu, który należy do jednego z typów wymienionych w atrybucie klasy procedury obsługi gestu.

3. Kliknij dwukrotnie dowolne miejsce na diagramie. Procedura obsługi dwukrotnego kliknięcia powinna być wywoływana.

4. Przeciągnij element z Eksploratora UML na diagram. Procedura obsługi przeciągania powinna być wywoływana.

   **Rozwiązywanie problemów**: Jeśli program obsługi gestu nie działa, upewnij się, że:

- Projekt procedury obsługi gestu jest wymieniony jako składnik MEF na karcie **zasoby** w pliku **source. Extensions. manifest** w projekcie VSIX.

- Parametry wszystkich atrybutów `Import` i `Export` są prawidłowe.

- Metoda `CanDragDrop` nie zwraca `false`.

- Typ diagramu modelu, którego używasz (Klasa UML, sekwencja i tak dalej) jest wymieniony jako jeden z atrybutów klasy obsługi gestów [ClassDesignerExtension], [SequenceDesignerExtension] i tak dalej.

- Brak wbudowanej funkcji zdefiniowanej już dla tego typu elementu docelowego i opuszczonego.

## <a name="Implementing"></a>Implementowanie obsługi gestu

### <a name="the-gesture-handler-methods"></a>Metody obsługi gestu
 Klasa procedury obsługi gestu implementuje i eksportuje <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>. Metody, które należy zdefiniować, są następujące:

|||
|-|-|
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Zwróć `true`, aby umożliwić porzucenie elementu źródłowego w `dragEvent` w tym miejscu docelowym.<br /><br /> Ta metoda nie powinna wprowadzać zmian w modelu. Powinna ona być szybka, ponieważ jest używana do określenia stanu strzałki, gdy użytkownik przesunie mysz.|
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Zaktualizuj model na podstawie obiektu źródłowego, do którego odwołuje się `dragEvent`, i celu.<br /><br /> Wywoływana, gdy użytkownik zwolni mysz po przeciągnięciu.|
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` to kształt kliknięty dwukrotnie przez użytkownika.|

 Programy obsługi można pisać, które mogą akceptować nie tylko UML, ale również różne inne elementy, takie jak pliki, węzły w widoku klasy .NET i tak dalej. Użytkownik może przeciągnąć dowolny z tych elementów na diagram UML, pod warunkiem, że piszesz metodę `OnDragDrop`, która może zdekodować serializowaną postać elementów. Metody dekodowania różnią się od jednego typu elementu do drugiego.

 Parametry tych metod są następujące:

- `ShapeElement target`., Kształt lub diagram, na którym użytkownik przełączył coś.

    `ShapeElement` jest klasą w implementacji, która opiera się na narzędziach modelowania UML. Aby zmniejszyć ryzyko umieszczenia modelu UML i diagramów w niespójnym stanie, zalecamy, aby nie używać metod tej klasy bezpośrednio. Zamiast tego zawiń element w `IShape`, a następnie użyj metod opisanych w temacie [Wyświetlanie modelu UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md).

  - Aby uzyskać `IShape`:

      ```
      IShape targetIShape = target.CreateIShape(target);
      ```

  - Aby uzyskać element modelu, który jest przeznaczony dla operacji przeciągania lub podwójnego kliknięcia:

      ```
      IElement target = targetIShape.Element;
      ```

      Można rzutować ten element na bardziej konkretny typ elementu.

  - Aby uzyskać magazyn modelu UML zawierający model UML:

      ```
      IModelStore modelStore =
        targetIShape.Element.GetModelStore(); 
      ```

  - Aby uzyskać dostęp do hosta i dostawcy usług:

      ```
      target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE
      ```

- `DiagramDragEventArgs eventArgs`., Ten parametr przenosi Zserializowany formularz obiektu źródłowego operacji przeciągania:

    ```
    System.Windows.Forms.IDataObject data = eventArgs.Data;
    ```

     Można przeciągać elementy wielu różnych rodzajów na diagram, z różnych części [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub z pulpitu systemu Windows. Różne typy elementów są zakodowane na różne sposoby w `IDataObject`. Aby wyodrębnić elementy z niej, zapoznaj się z dokumentacją odpowiedniego typu obiektu.

     Jeśli obiekt źródłowy jest elementem UML przeciąganym z Eksploratora modelu UML lub z innego diagramu UML, zapoznaj się z tematem [Pobieranie elementów modelu UML z IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

### <a name="writing-the-code-of-the-methods"></a>Pisanie kodu metod
 Aby uzyskać więcej informacji na temat pisania kodu w celu odczytania i zaktualizowania modelu, zobacz [Programowanie przy użyciu interfejsu API UML](../modeling/programming-with-the-uml-api.md).

 Aby uzyskać informacje o uzyskiwaniu dostępu do informacji o modelu w operacji przeciągania, zobacz [Pobieranie elementów modelu UML z IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

 Jeśli pracujesz z diagramem sekwencji, zobacz też [Edytowanie diagramów sekwencji UML przy użyciu interfejsu API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Oprócz parametrów metod, można również zadeklarować zaimportowaną właściwość w klasie, która zapewnia dostęp do bieżącego diagramu i modelu.

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 Deklaracja `IDiagramContext` umożliwia pisanie kodu w metodach, które uzyskują dostęp do diagramu, bieżącego wyboru i modelu:

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

## <a name="Installing"></a>Instalowanie i odinstalowywanie rozszerzenia
 Rozszerzenie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] można zainstalować zarówno na swoim komputerze, jak i na innych komputerach.

#### <a name="to-install-an-extension"></a>Aby zainstalować rozszerzenie

1. Na komputerze Znajdź plik **. vsix** , który został skompilowany przez projekt VSIX.

    1. W **Eksplorator rozwiązań**, w menu skrótów projektu VSIX, wybierz polecenie **Otwórz folder w Eksploratorze Windows**.

    2. Zlokalizuj plik **bin \\ \* \\** _YourProject_ **. vsix**

2. Skopiuj plik **. vsix** do komputera docelowego, na którym chcesz zainstalować rozszerzenie. Może to być własny komputer lub inny.

     Komputer docelowy musi mieć jedną z wersji [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] określonych w elemencie **source. Extension. vsixmanifest**.

3. Na komputerze docelowym otwórz plik **. vsix** .

     Zostanie otwarty **Instalator rozszerzenia programu Visual Studio** , który zainstaluje rozszerzenie.

4. Uruchom lub Uruchom ponownie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Aby odinstalować rozszerzenie

1. W menu **Narzędzia** wybierz pozycję **rozszerzenia i aktualizacje**.

2. Rozwiń **zainstalowane rozszerzenia**.

3. Wybierz rozszerzenie, a następnie wybierz **Odinstaluj**.

   Rzadko błędne rozszerzenie nie zostanie załadowane i tworzy raport w oknie błędu, ale nie jest wyświetlany w Menedżerze rozszerzeń. W takim przypadku można usunąć rozszerzenie, usuwając plik z:

   *% LocalAppData%* **\Local\Microsoft\VisualStudio \\ [wersja] \Extensions**

## <a name="DragExample"></a>Przyklad
 Poniższy przykład pokazuje, jak utworzyć linie życia w diagramie sekwencji na podstawie części i portów składnika przeciąganych z diagramu składników.

 Aby go przetestować, naciśnij klawisz F5. Zostanie otwarte doświadczalne wystąpienie programu Visual Studio. W tym przypadku należy otworzyć model UML i utworzyć składnik na diagramie składników. Dodaj do tego składnika niektóre interfejsy i wewnętrzne części składników. Wybierz interfejsy i części. Następnie przeciągnij interfejsy i części na diagram sekwencji. (Przeciągnij ze diagramu składnika do karty dla diagramu sekwencji, a następnie w dół do diagramu sekwencji). Linia życia będzie wyświetlana dla każdego interfejsu i części.

 Aby uzyskać więcej informacji na temat powiązań interakcji z diagramami sekwencji, zobacz [Edytowanie diagramów sekwencji UML przy użyciu interfejsu API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

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

 Kod `GetModelElementsFromDragEvent()` został opisany w artykule [Pobieranie elementów modelu UML z IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

## <a name="see-also"></a>Zobacz też
 [Definiowanie i Instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md) [Rozszerzanie modeli UML i diagramów](../modeling/extend-uml-models-and-diagrams.md) [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Definiowanie ograniczeń walidacji dla programowania modeli UML](../modeling/define-validation-constraints-for-uml-models.md) [przy użyciu interfejsu API UML](../modeling/programming-with-the-uml-api.md)
