---
title: 'Instrukcje: dostęp i ograniczenie bieżącego zaznaczenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
ms.assetid: 2990981e-dfae-416f-b0d0-7197f1242dfa
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00fa99ce9be158b2fe7b0bc4076817892a1b1ba9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646232"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Porady: ograniczenie bieżącego wyboru i uzyskiwanie dostępu do niego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy piszesz polecenie lub program obsługi gestu dla języka specyficznego dla domeny, możesz określić, jaki element użytkownik kliknął prawym przyciskiem myszy. Możesz również uniemożliwić wybranie niektórych kształtów lub pól. Na przykład można ustawić, że gdy użytkownik kliknie ikonę dekoratora, w zamian zostanie wybrany kształt zawierający ją. Ograniczanie wyboru w ten sposób zmniejsza liczbę programów obsługi, które należy napisać. Ułatwia to również użytkownikom, którzy mogą kliknąć gdziekolwiek w kształcie, bez konieczności uniknięcia dekoratora.

## <a name="accessing-the-current-selection-from-a-command-handler"></a>Uzyskiwanie dostępu do bieżącego zaznaczenia z programu obsługi poleceń
 Klasa zestawu poleceń dla języka specyficznego dla domeny zawiera programy obsługi poleceń dla poleceń niestandardowych. Klasa <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>, z której pochodzi Klasa zestawu poleceń dla języka specyficznego dla domeny, zawiera kilku członków do uzyskiwania dostępu do bieżącego zaznaczenia.

 W zależności od polecenia program obsługi poleceń może potrzebować wyboru w projektancie modeli, Eksploratorze modelu lub aktywnym oknie.

#### <a name="to-access-selection-information"></a>Aby uzyskać dostęp do informacji o wyborze

1. Klasa <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> definiuje następujące elementy członkowskie, których można użyć w celu uzyskania dostępu do bieżącego zaznaczenia.

    |Element członkowski|Opis|
    |------------|-----------------|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>, Metoda|Zwraca `true`, jeśli którykolwiek z elementów zaznaczonych w projektancie modeli jest kształtem przedziału; w przeciwnym razie `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>, Metoda|Zwraca `true`, jeśli diagram został wybrany w projektancie modeli; w przeciwnym razie `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>, Metoda|Zwraca `true`, jeśli wybrano dokładnie jeden element w projektancie modeli; w przeciwnym razie `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>, Metoda|Zwraca `true`, jeśli wybrano dokładnie jeden element w aktywnym oknie; w przeciwnym razie `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> Właściwość|Pobiera kolekcję tylko do odczytu elementów wybranych w projektancie modeli.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> Właściwość|Pobiera kolekcję tylko do odczytu elementów wybranych w aktywnym oknie.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> Właściwość|Pobiera element podstawowy zaznaczenia w projektancie modeli.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> Właściwość|Pobiera element podstawowy zaznaczenia w aktywnym oknie.|

2. Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> klasy <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> zapewnia dostęp do obiektu <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>, który reprezentuje okno projektanta modelu i zapewnia dodatkowy dostęp do wybranych elementów w projektancie modeli.

3. Ponadto wygenerowany kod definiuje Właściwość okna narzędzia Eksploratora i Właściwość wybór Eksploratora w klasie zestawu poleceń dla języka specyficznego dla domeny.

    - Właściwość okna narzędzia Eksploratora zwraca wystąpienie klasy okna narzędzi Eksploratora dla języka specyficznego dla domeny. Klasa okna narzędzi Eksploratora pochodzi z klasy <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> i reprezentuje Eksploratora modeli dla języka specyficznego dla domeny.

    - Właściwość `ExplorerSelection` zwraca wybrany element w oknie Eksplorator modelu dla języka specyficznego dla domeny.

## <a name="determining-which-window-is-active"></a>Określanie, które okno jest aktywne
 Interfejs <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> zawiera definicje elementów członkowskich, które zapewniają dostęp do bieżącego stanu zaznaczenia w powłoce. Obiekt <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> można uzyskać z klasy pakietu lub klasy zestawu poleceń dla języka specyficznego dla domeny za pomocą właściwości `MonitorSelection` zdefiniowanej w klasie bazowej każdej z nich. Klasa pakietu pochodzi z klasy <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>, a Klasa zestawu poleceń pochodzi od klasy <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

#### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Aby określić, jaki typ okna jest aktywny w programie obsługi poleceń

1. Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> klasy <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> zwraca obiekt <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>, który zapewnia dostęp do bieżącego stanu zaznaczenia w powłoce.

2. Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> interfejsu <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> pobiera aktywny kontener wyboru, który może się różnić od aktywnego okna.

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

## <a name="constraining-the-selection"></a>Ograniczanie zaznaczenia
 Dodając reguły wyboru, można kontrolować, które elementy są wybierane, gdy użytkownik wybierze element w modelu. Na przykład, aby zezwolić użytkownikowi na traktowanie wielu elementów jako pojedynczej jednostki, można użyć reguły wyboru.

#### <a name="to-create-a-selection-rule"></a>Aby utworzyć regułę wyboru

1. Tworzenie niestandardowego pliku kodu w projekcie DSL

2. Zdefiniuj klasę reguły wyboru, która jest pochodną klasy <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>.

3. Zastąp metodę <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> klasy reguł wyboru, aby zastosować kryteria wyboru.

4. Dodaj definicję klasy częściowej dla klasy ClassDiagram do pliku kodu niestandardowego.

     Klasa `ClassDiagram` dziedziczy z klasy <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> i jest zdefiniowana w wygenerowanym pliku kodu, Diagram.cs, w projekcie DSL.

5. Zastąp Właściwość <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> klasy `ClassDiagram`, aby zwracała regułę wyboru niestandardowego.

     Domyślna implementacja właściwości <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> pobiera obiekt reguły wyboru, który nie modyfikuje zaznaczenia.

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
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet><xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>
