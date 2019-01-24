---
title: 'Instrukcje: Dostęp i ograniczyć bieżące zaznaczenie | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
ms.assetid: 2990981e-dfae-416f-b0d0-7197f1242dfa
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 731968f79565742595b4f574e986d69a311d5f90
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769624"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Instrukcje: Ograniczanie bieżącego wyboru i uzyskiwanie dostępu do niego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kiedy piszesz obsługi polecenia lub gestu dla języka specyficznego dla domeny, można określić elementu użytkownik kliknął prawym przyciskiem myszy. Można również uniemożliwić niektórych kształtów lub pól są zaznaczone. Na przykład można rozmieścić, że po kliknięciu ikony dekorator kształtu, który go zawiera zamian zostanie wybrany. Ograniczając zaznaczenia w ten sposób powoduje zmniejszenie liczby programów obsługi, które trzeba napisać. Ponadto ułatwia dla użytkownika, który może kliknij w dowolnym miejscu w kształcie bez konieczności uniknąć dekoratora.  
  
## <a name="accessing-the-current-selection-from-a-command-handler"></a>Uzyskiwanie dostępu do bieżącego zaznaczenia z programem obsługi.  
 Klasy zestaw poleceń języka specyficznego dla domeny zawiera programy obsługi poleceń do niestandardowych poleceń. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasy, z którego pochodzi klasy zestaw poleceń języka specyficznego dla domeny, zapewnia kilka elementów członkowskich do uzyskiwania dostępu do bieżącego zaznaczenia.  
  
 W zależności od polecenia program obsługi poleceń może być konieczne zaznaczenie w Projektancie modeli, Eksplorator modelu lub aktywnego okna.  
  
#### <a name="to-access-selection-information"></a>Dostęp do informacji o wybór  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasa definiuje następujące elementy członkowskie, które mogą służyć do dostępu do bieżącego zaznaczenia.  
  
    |Element członkowski|Opis|  
    |------------|-----------------|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> — Metoda|Zwraca `true` elementy zaznaczone w Projektancie modeli w przypadku kształt przedziału; w przeciwnym razie `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> — Metoda|Zwraca `true` Jeśli diagram jest wybrane w Projektancie modeli; w przeciwnym razie `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> — Metoda|Zwraca `true` Jeśli dokładnie jeden element jest wybrany w Projektancie modeli; w przeciwnym razie `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> — Metoda|Zwraca `true` Jeśli dokładnie jeden element jest wybrany w aktywnym oknie; w przeciwnym razie `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> Właściwość|Pobiera kolekcję tylko do odczytu elementy zaznaczone w Projektancie modeli.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> Właściwość|Pobiera kolekcję tylko do odczytu elementów wybrano aktywnego okna.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> Właściwość|Pobiera podstawowy element zaznaczenia w Projektancie modeli.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> Właściwość|Pobiera podstawowy element wyboru aktywnego okna.|  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy zapewnia dostęp do <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> obiekt, który reprezentuje oknie projektanta modeli i zapewnia dodatkowe prawa dostępu wybranych elementów w Projektancie modeli.  
  
3.  Ponadto wygenerowanego kodu definiuje właściwość okna narzędzia Eksploratora i Eksplorator właściwości zaznaczenia w poleceniu set — Klasa języka specyficznego dla domeny.  
  
    -   Właściwość okna narzędzia Eksploratora Zwraca wystąpienie klasy okna narzędzia Eksploratora dla języka specyficznego dla domeny. Pochodną klasy okna narzędzia Eksploratora <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> klasy i reprezentuje Eksploratora modelu dla języka specyficznego dla domeny.  
  
    -   `ExplorerSelection` Właściwość zwraca wybranego elementu w oknie Eksploratora modelu dla języka specyficznego dla domeny.  
  
## <a name="determining-which-window-is-active"></a>Określanie, które okno jest aktywne  
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Zawiera interfejs definiuje członków, które zapewniają dostęp do bieżącego stanu zaznaczenia w powłoce. Możesz uzyskać <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> obiektów w klasie pakietu lub klasy zestawu poleceń dla języka specyficznego dla domeny, za pośrednictwem `MonitorSelection` właściwości zdefiniowanej w klasie bazowej każdego z nich. Klasa pakiet pochodzi z <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> klasy, a polecenie zestawu pochodzi od klasy <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy.  
  
#### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Aby określić z obsługi polecenia, jakiego rodzaju okno jest aktywne  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy zwraca <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> obiektu, który zapewnia dostęp do bieżącego stanu zaznaczenia w powłoce.  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interfejs otrzymuje kontenera aktywnego zaznaczenia, które mogą różnić się od aktywnego okna.  
  
3.  Dodaj następujące właściwości do polecenia set — klasa dla Ciebie języka specyficznego dla domeny, aby ustalić, jakiego rodzaju okno jest aktywne.  
  
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
  
## <a name="constraining-the-selection"></a>Ograniczając zaznaczenie  
 Przez dodanie reguł zaznaczenia, można kontrolować, które elementy są zaznaczone, gdy użytkownik wybierze element w modelu. Na przykład aby umożliwić użytkownikowi traktować liczbę elementów jako pojedynczą jednostkę, można użyć reguła wyboru.  
  
#### <a name="to-create-a-selection-rule"></a>Aby utworzyć regułę zaznaczenia  
  
1.  Utwórz plik niestandardowego kodu w projekcie języka DSL  
  
2.  Definiowanie klasy reguła wyboru, która jest tworzony na podstawie <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> klasy.  
  
3.  Zastąp <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> metody klasy reguła wyboru do zastosowania kryteriów wyboru.  
  
4.  Dodaj definicję klasy częściowej klasy ClassDiagram do pliku kodu niestandardowego.  
  
     `ClassDiagram` Klasa pochodzi od <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> klasy i jest zdefiniowana w pliku wygenerowanego kodu, Diagram.cs, w projekcie języka DSL.  
  
5.  Zastąp <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> właściwość `ClassDiagram` klasy w celu zwrócenia reguły niestandardowy wybór.  
  
     Domyślna implementacja klasy <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> właściwości pobiera obiekt reguła wyboru, który nie powoduje modyfikacji zaznaczenia.  
  
### <a name="example"></a>Przykład  
 Następujący plik kodu jest tworzona reguła wyboru rozwijany wyboru, aby uwzględnić wszystkie wystąpienia został początkowo zaznaczone kształty domeny.  
  
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
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>
