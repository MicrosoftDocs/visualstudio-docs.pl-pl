---
title: 'Porady: ograniczenie bieżącego wyboru i uzyskiwanie dostępu do niego'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1f5aaa106e00f9b10eb88892bcc978b92a01c79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545694"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Porady: ograniczenie bieżącego wyboru i uzyskiwanie dostępu do niego

Gdy piszesz polecenie lub program obsługi gestu dla języka specyficznego dla domeny, możesz określić, jaki element użytkownik kliknął prawym przyciskiem myszy. Możesz również uniemożliwić wybranie niektórych kształtów lub pól. Na przykład można ustawić, że gdy użytkownik kliknie ikonę dekoratora, w zamian zostanie wybrany kształt zawierający ją. Ograniczanie wyboru w ten sposób zmniejsza liczbę programów obsługi, które należy napisać. Ułatwia to również użytkownikom, którzy mogą kliknąć gdziekolwiek w kształcie, bez konieczności uniknięcia dekoratora.

## <a name="access-the-current-selection-from-a-command-handler"></a>Dostęp do bieżącego zaznaczenia z programu obsługi poleceń

Klasa zestawu poleceń dla języka specyficznego dla domeny zawiera programy obsługi poleceń dla poleceń niestandardowych. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>Klasa, z której pochodzi Klasa zestawu poleceń dla języka specyficznego dla domeny, zawiera kilku członków do uzyskiwania dostępu do bieżącego zaznaczenia.

W zależności od polecenia program obsługi poleceń może potrzebować wyboru w projektancie modeli, Eksploratorze modelu lub aktywnym oknie.

### <a name="to-access-selection-information"></a>Aby uzyskać dostęp do informacji o wyborze

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>Klasa definiuje następujące elementy członkowskie, których można użyć w celu uzyskania dostępu do bieżącego zaznaczenia.

    |Członek|Opis|
    |-|-|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Zwraca `true` Jeśli którykolwiek z elementów zaznaczonych w projektancie modeli jest kształtem przedziału; w przeciwnym razie `false` .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Zwraca `true` Jeśli diagram został wybrany w projektancie modeli; w przeciwnym razie `false` .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Zwraca `true` w przypadku wybrania dokładnie jednego elementu w projektancie modeli; w przeciwnym razie `false` .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Zwraca `true` w przypadku wybrania dokładnie jednego elementu w aktywnym oknie; w przeciwnym razie `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> wartość|Pobiera kolekcję tylko do odczytu elementów wybranych w projektancie modeli.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> wartość|Pobiera kolekcję tylko do odczytu elementów wybranych w aktywnym oknie.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> wartość|Pobiera element podstawowy zaznaczenia w projektancie modeli.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> wartość|Pobiera element podstawowy zaznaczenia w aktywnym oknie.|

2. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy zapewnia dostęp do <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> obiektu, który reprezentuje okno projektanta modelu i zapewnia dodatkowy dostęp do wybranych elementów w projektancie modeli.

3. Ponadto wygenerowany kod definiuje Właściwość okna narzędzia Eksploratora i Właściwość wybór Eksploratora w klasie zestawu poleceń dla języka specyficznego dla domeny.

    - Właściwość okna narzędzia Eksploratora zwraca wystąpienie klasy okna narzędzi Eksploratora dla języka specyficznego dla domeny. Klasa okna narzędzi Eksploratora pochodzi z <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> klasy i reprezentuje Eksploratora modeli dla języka specyficznego dla domeny.

    - `ExplorerSelection`Właściwość zwraca wybrany element w oknie Eksplorator modelu dla języka specyficznego dla domeny.

## <a name="determine-which-window-is-active"></a>Ustal, które okno jest aktywne

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>Interfejs zawiera definicje elementów członkowskich, które zapewniają dostęp do bieżącego stanu zaznaczenia w powłoce. Można pobrać <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> obiekt z klasy pakietu lub klasy zestawu poleceń dla języka specyficznego dla domeny za pośrednictwem `MonitorSelection` właściwości zdefiniowanej w klasie bazowej każdej z nich. Klasa pakietu pochodzi z <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> klasy, a Klasa zestawu poleceń pochodzi od <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Aby określić, jaki typ okna jest aktywny w programie obsługi poleceń

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy zwraca <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> obiekt, który zapewnia dostęp do bieżącego stanu zaznaczenia w powłoce.

2. <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interfejsu pobiera aktywny kontener wyboru, który może się różnić od aktywnego okna.

3. Dodaj następujące właściwości do klasy zestawu poleceń dla języka specyficznego dla domeny, aby określić, jakiego typu okno jest aktywne.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Ogranicz wybór

Dodając reguły wyboru, można kontrolować, które elementy są wybierane, gdy użytkownik wybierze element w modelu. Na przykład, aby zezwolić użytkownikowi na traktowanie wielu elementów jako pojedynczej jednostki, można użyć reguły wyboru.

### <a name="to-create-a-selection-rule"></a>Aby utworzyć regułę wyboru

1. Tworzenie niestandardowego pliku kodu w projekcie DSL

2. Zdefiniuj klasę reguł wyboru, która jest pochodną <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> klasy.

3. Zastąp <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> metodę klasy reguły wyboru, aby zastosować kryteria wyboru.

4. Dodaj definicję klasy częściowej dla klasy ClassDiagram do pliku kodu niestandardowego.

     `ClassDiagram`Klasa pochodzi z <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> klasy i jest zdefiniowana w wygenerowanym pliku kodu, diagram.cs, w projekcie DSL.

5. Zastąp <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> Właściwość klasy, `ClassDiagram` aby zwracała regułę wyboru niestandardowego.

     Domyślna implementacja <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> Właściwości pobiera obiekt reguły wyboru, który nie modyfikuje zaznaczenia.

### <a name="example"></a>Przykład

Poniższy plik kodu tworzy regułę wyboru, która rozszerza zaznaczenie, aby uwzględnić wszystkie wystąpienia każdego z wcześniej wybranych kształtów domeny.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>