---
title: 'Porady: ograniczenie bieżącego wyboru i uzyskiwanie dostępu do niego'
description: Dowiedz się, jak określić, który element użytkownik kliknął prawym przyciskiem myszy podczas pisania polecenia lub procedury obsługi gestów dla języka specyficznego dla domeny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 28d0f99743535965b3cf203d461fac5d0193607c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386608"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Porady: ograniczenie bieżącego wyboru i uzyskiwanie dostępu do niego

Podczas pisania polecenia lub procedury obsługi gestów dla języka specyficznego dla domeny można określić, który element użytkownik kliknął prawym przyciskiem myszy. Możesz również uniemożliwić wybrane kształty lub pola. Można na przykład rozmieścić, że gdy użytkownik kliknie ikonę dekoratora, zostanie wybrany kształt, który go zawiera. Ograniczenie wyboru w ten sposób zmniejsza liczbę programów obsługi, które trzeba zapisać. Ułatwia to również użytkownikowi, który może kliknąć dowolne miejsce w kształcie bez konieczności unikania dekoratora.

## <a name="access-the-current-selection-from-a-command-handler"></a>Uzyskiwanie dostępu do bieżącego wyboru z programu obsługi poleceń

Klasa zestawu poleceń dla języka specyficznego dla domeny zawiera programy obsługi poleceń dla poleceń niestandardowych. Klasa, z której pochodzi klasa zestawu poleceń dla języka specyficznego dla domeny, udostępnia kilka elementów członkowskich do uzyskiwania dostępu <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> do bieżącego wyboru.

W zależności od polecenia program obsługi poleceń może wymagać wyboru w projektancie modeli, eksploratorze modeli lub aktywnym oknie.

### <a name="to-access-selection-information"></a>Aby uzyskać dostęp do informacji o wyborze

1. Klasa <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> definiuje następujące składowe, których można użyć do uzyskania dostępu do bieżącego wyboru.

    |Członek|Opis|
    |-|-|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Zwraca `true` wartość , jeśli którykolwiek z elementów wybranych w projektancie modelu ma kształt przedziału. W przeciwnym razie zwraca wartość `false` .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Zwraca `true` wartość , jeśli diagram został wybrany w projektancie modeli; w przeciwnym razie zwraca wartość `false` .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Zwraca `true` wartość , jeśli w projektancie modeli wybrano dokładnie jeden element. W przeciwnym razie zwraca wartość `false` .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Zwraca `true` wartość , jeśli w aktywnym oknie wybrano dokładnie jeden element. W przeciwnym razie zwraca wartość `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> Właściwość|Pobiera kolekcję tylko do odczytu elementów wybranych w projektancie modeli.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> Właściwość|Pobiera kolekcję tylko do odczytu elementów wybranych w aktywnym oknie.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> Właściwość|Pobiera podstawowy element zaznaczenia w projektancie modeli.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> Właściwość|Pobiera podstawowy element zaznaczenia w aktywnym oknie.|

2. Właściwość klasy zapewnia dostęp do obiektu reprezentującego okno projektanta modelu i zapewnia dodatkowy dostęp do wybranych elementów <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> w <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> projektancie modeli.

3. Ponadto wygenerowany kod definiuje właściwość okna narzędzi eksploratora i właściwość wyboru eksploratora w klasie zestawu poleceń dla języka specyficznego dla domeny.

    - Właściwość okna narzędzi eksploratora zwraca wystąpienie klasy okna narzędzi eksploratora dla języka specyficznego dla domeny. Klasa okna narzędzi eksploratora pochodzi od klasy <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> i reprezentuje eksploratora modelu dla języka specyficznego dla domeny.

    - Właściwość `ExplorerSelection` zwraca wybrany element w oknie eksploratora modelu dla języka specyficznego dla domeny.

## <a name="determine-which-window-is-active"></a>Określanie, które okno jest aktywne

Interfejs <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> zawiera definicje elementów członkowskich, które zapewniają dostęp do bieżącego stanu wyboru w powłoki. Obiekt można pobrać z klasy pakietu lub klasy zestawu poleceń dla języka specyficznego dla domeny za pośrednictwem właściwości zdefiniowanej w klasie bazowej każdego z <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> `MonitorSelection` nich. Klasa pakietu pochodzi od klasy , a klasa zestawu poleceń pochodzi <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> od <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy .

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Aby określić na podstawie programu obsługi poleceń, jakiego typu okno jest aktywne

1. Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> klasy zwraca obiekt , który zapewnia dostęp do <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> bieżącego stanu zaznaczenia w powłokie.

2. Właściwość interfejsu pobiera aktywny kontener wyboru, który może różnić się <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> od aktywnego okna.

3. Dodaj następujące właściwości do klasy zestawu poleceń dla języka specyficznego dla domeny, aby określić, jaki typ okna jest aktywny.

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

## <a name="constrain-the-selection"></a>Ograniczanie zaznaczenia

Dodając reguły wyboru, możesz kontrolować, które elementy są wybierane, gdy użytkownik wybierze element w modelu. Aby na przykład umożliwić użytkownikowi traktowanie wielu elementów jako pojedynczej jednostki, można użyć reguły wyboru.

### <a name="to-create-a-selection-rule"></a>Aby utworzyć regułę wyboru

1. Tworzenie niestandardowego pliku kodu w projekcie DSL

2. Zdefiniuj klasę reguły wyboru pochodzącą od <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> klasy .

3. Zastąp <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> metodę klasy reguły wyboru, aby zastosować kryteria wyboru.

4. Dodaj definicję klasy częściowej dla klasy ClassDiagram do pliku kodu niestandardowego.

     Klasa pochodzi od klasy i jest zdefiniowana w wygenerowanym pliku kodu `ClassDiagram` <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> Diagram.cs w projekcie DSL.

5. Zastąp <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> właściwość klasy `ClassDiagram` , aby zwrócić niestandardową regułę wyboru.

     Domyślna implementacja <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> właściwości pobiera obiekt reguły wyboru, który nie modyfikuje zaznaczenia.

### <a name="example"></a>Przykład

Poniższy plik kodu tworzy regułę wyboru, która rozszerza zaznaczenie, aby uwzględnić wszystkie wystąpienia każdego z początkowo wybranych kształtów domeny.

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