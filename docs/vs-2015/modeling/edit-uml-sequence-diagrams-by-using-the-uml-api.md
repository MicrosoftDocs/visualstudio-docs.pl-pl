---
title: Edytowanie diagramów sekwencji UML przy użyciu interfejsu API UML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f68cf87a7f45b906c6de43e0a837d49132b7a3e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725562"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>Edytowanie diagramów sekwencji UML przy użyciu interfejsu API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interakcja to sekwencję wiadomości między liniami życia. Interakcji są wyświetlane na diagramie sekwencji UML.  
  
 Aby uzyskać szczegółowe informacje o interfejsie API, zobacz <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>.  
  
 Aby uzyskać bardziej ogólne wprowadzenie do pisania poleceń i program obsługi gestów do diagramów UML, zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="basic-code"></a>Podstawową kodu  
  
### <a name="namespace-imports"></a>Importuje Namespace  
 Należy uwzględnić następujące `using` instrukcji:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
   // for basic UML types such as IPackage  
using Microsoft.VisualStudio.Uml.Interactions;  
   // for interaction types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // to create elements and use additional functions  
```  
  
 Jeśli tworzysz poleceń menu i procedury obsługi gestów, należy również:  
  
```  
using System.ComponentModel.Composition;   
   // for Import and Export  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   // for ICommandExtension  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   // for diagrams and context  
```  
  
 Aby uzyskać więcej informacji, zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="getting-the-context"></a>Pobieranie kontekstu  
 Jeśli edytujesz interakcji w ramach obsługi polecenia lub gestu w diagramie sekwencji można uzyskać odwołania do kontekstu. Na przykład:  
  
```  
[SequenceDesignerExtension]  
[Export(typeof(ICommandExtension))]    
public class MySequenceDiagramCommand : ICommandExtension  
{  
    [Import]  
    public IDiagramContext Context { get; set; }  
    public void QueryStatus (IMenuCommand command)  
    {  
      ISequenceDiagram sequenceDiagram =   
          Context.CurrentDiagram as ISequenceDiagram;  
         ...  
```  
  
### <a name="generated-and-uml-sequence-diagrams"></a>Wygenerowany i diagramów sekwencji UML  
 Istnieją dwa rodzaje diagramów sekwencji: te, które zostały ręcznie utworzone w projekcie modelowania UML i tych, które zostały wygenerowane z kodu programu. Użyj `UmlMode` właściwość, aby dowiedzieć się, jaka sekwencja diagramu można mieć.  
  
> [!NOTE]
>  Ta właściwość zwraca wartość FAŁSZ tylko w przypadku diagramy sekwencji wygenerowane z kodu za pomocą programu Visual Studio 2013 i starszych. Obejmuje to sekwencję wygenerowany kod, diagramy migracji z 2013 i starszych wersji. Ta wersja programu Visual Studio nie obsługuje generowania nowych diagramów sekwencji.  
  
 Na przykład, jeśli chcesz utworzyć polecenie menu, która jest widoczna tylko na diagramach sekwencji UML a następnie `QueryStatus()` metoda może zawierać następującą instrukcję:  
  
```  
command.Enabled = command.Visible =   
      sequenceDiagram != null && sequenceDiagram.UmlMode;  
```  
  
 Sekwencji wygenerowane diagram, linii życia, wiadomości i inne elementy są prawie takie same jak w diagramie sekwencji UML. W modelu UML Store modelu ma główny, który jest Model, który jest właścicielem wszystkich innych elementów. Jednak wygenerowane interakcji istnieje w własnej Store modelu, który ma główną o wartości null:  
  
```  
IModel rootModel = sequenceDiagram.ModelStore.Root;  
    // !sequenceDiagram.UmlMode == (rootModel == null)  
```  
  
## <a name="to-create-and-display-an-interaction"></a>Aby utworzyć i wyświetlić interakcji  
 Utwórz interakcji jako element podrzędny pakietu lub modelu.  
  
 Na przykład jeśli tworzysz polecenie, które mogą być wykonywane na pusty diagram sekwencji, należy zawsze zacząć, sprawdzając, czy istnieje interakcja.  
  
```  
public void Execute (IMenuCommand command)  
{  
    ISequenceDiagram sequenceDiagram =   
         Context.CurrentDiagram as ISequenceDiagram;  
    if (sequenceDiagram == null) return;  
    // Get the diagram's interaction:  
    IInteraction interaction = sequenceDiagram.Interaction;  
    // A new sequence diagram might have no interaction:  
    if (interaction == null)  
    {  
       // Get the home package or model of the diagram:  
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();  
       interaction = parentPackage.CreateInteraction();  
       // Display the interaction on the sequence diagram:  
       sequenceDiagram.Bind(interaction);  
    }   
```  
  
## <a name="updating-an-interaction-and-its-layout"></a>Aktualizowanie interakcji i jego układ  
 Po zaktualizowaniu interakcji zawsze zakończyć operację, aktualizując jej układ przy użyciu jednej z następujących metod:  
  
- `ISequenceDiagram.UpdateShapePositions()` Ustawia położenie kształty, które niedawno zostało wstawionych lub przeniesiona i ich kształtów sąsiednich.  
  
- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` odrysowuje cały diagram. Parametr służy do określania położenia linie życia i/lub komunikaty.  
  
  Jest to szczególnie ważne podczas wstawiania nowych elementów lub Przenieś istniejące elementy. Nie będą w właściwe pozycje na diagramie do momentu, kiedy została wykonana jedna z tych operacji. Musisz wywołać jedną z tych operacji, po upływie szereg zmian.  
  
  Aby uniknąć bemusing użytkownika wykonującego cofania po polecenia, użyj `ILinkedUndoTransaction` należy ująć zmiany, a końcowe `Layout()` lub `UpdateShapePositions()` operacji. Na przykład:  
  
```  
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))  
{  
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);  
  Diagram.UpdateShapePositions();  
  transaction.Commit();  
}  
```  
  
 Aby użyć `ILinkedUndoTransaction`, musisz wprowadzić tę deklarację klasy:  
  
```  
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }  
```  
  
 Aby uzyskać więcej informacji, zobacz [aktualizacji modelu UML łącza za pomocą transakcji](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
## <a name="building-an-interaction"></a>Tworzenie interakcji  
  
### <a name="to-create-lifelines"></a>Do utworzenia linii życia  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
```  
  
 Linia życia reprezentuje element składnika, oznacza to, że wystąpienie typu. Na przykład jeśli interakcji jest używany do pokazywania, jak składnik deleguje komunikatów przychodzących do jego wewnętrznych części, linie życia może reprezentować portów i części składnika:  
  
```  
foreach (IConnectableElement part in   
            component.Parts  
           .Concat<IConnectableElement>(component.OwnedPorts))  
{  
   ILifeline lifeline = interaction.CreateLifeline();  
   lifeline.Represents = part;  
}  
```  
  
 Jeśli interakcji zawiera dowolny zestaw obiektów, możesz też utworzyć właściwości lub innych `IConnectableElement` w samej interakcji:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
IProperty property1 = interaction.CreateProperty();  
property1.Type = model.CreateInterface();  
property1.Type.Name = "Type 1";  
lifeline.Represents = property1;  
```  
  
 Również Alternatywnie można ustawić nazwę i typ linii życia, bez powiązania go z elementem składnika:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
lifeline.Name = "c1";  
lifeline.SetInstanceType("Customer");  
System.Diagnostics.Debug.Assert(  
           lifeline.GetDisplayName() == "c1:Customer"  );  
```  
  
### <a name="to-create-messages"></a>Aby utworzyć wiadomości  
 Aby utworzyć komunikat, należy zidentyfikować punkty wstawienia na źródłowej i docelowej linii życia. Na przykład:  
  
```  
interaction.CreateMessage( sourceInsertionPoint,   
                           targetInsertionPoint,   
                           MessageKind.Complete,   
                           MessageSort.ASynchCall)  
```  
  
 Aby utworzyć komunikat, który ma niezdefiniowane źródłowa lub docelowa niezdefiniowane:  
  
```  
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);  
```  
  
 Istnieje kilka wiadomości, które można użyć, aby zidentyfikować punkty wstawienia na wszystkich kluczowych zagadnieniach na linii życia:  
  
|Metoda ILifeline|Umożliwia wstawianie w tym momencie|  
|-------------------------|------------------------------------|  
|`FindInsertionPointAtTop()`|Górnej linii życia.|  
|`FindInsertionPointAtBottom()`|Na koniec linii życia.|  
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Punkt natychmiast po określony komunikat.|  
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|Punkt, może być na linii życia lub na nadrzędny blok specyfikacji wykonywania.|  
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Punkt następujące wykorzystanie interakcji.|  
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Punkt następującego fragmentu w połączeniu.|  
|`FindInsertionPoint(IExecutionSpecification block)`|Górnej części bloku wykonywania.|  
|`FindInsertionPoint(IInteractionOperand fragment)`|Górnej operand połączonego fragmentu.|  
  
 Podczas tworzenia wiadomości powinien zachować ostrożność, aby uniknąć Definiowanie komunikat, który będzie skrzyżowany kolejną wiadomość.  
  
### <a name="to-create-combined-fragments-and-interaction-uses"></a>Do utworzenia połączonego fragmentu i zastosowania interakcji  
 Można utworzyć połączonego fragmentu i używa interakcji, określając punkt wstawiania w poszczególnych linii życia, które muszą zostać uwzględnione w elementu. Należy zadbać, aby uniknąć określania zestaw punktów przecinających przez istniejącą wiadomość lub fragmentu.  
  
```  
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,   
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
Interaction.CreateInteractionUse(  
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
```  
  
 Można również utworzyć połączony fragment, który obejmuje istniejącego zestawu komunikatów. Komunikaty muszą rozwijani w tej samej linii życia lub wykonanie bloku.  
  
```  
ICombinedFragment cf = Interaction.CreateCombinedFragment(  
  InteractionOperatorKind.Loop,  
  Interaction.Lifelines.First().GetAllOutgoingMessages());  
```  
  
 Połączony fragment zawsze jest tworzony z jednym argumentem. Aby utworzyć nowy argument operacji, należy określić istniejące argument, który ma zostać wstawiony przed lub po oraz czy ma zostać wstawiony po nim lub przed nią:  
  
```  
// Create an additional operand before the first  
cf.CreateInteractionOperand(cf.Operands.First(), false);  
// Create an additional operand after the last:  
cf.CreateInteractionOperand(cf.Operands.Last(), true);  
```  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Jeśli zmiany nie są wykonywane przy użyciu kształtów pojawi się w pozycji niepoprawne `UpdateShapePositions()` lub `Layout()` operacji.  
  
 Inne problemy są spowodowane przez punkty wstawienia trwa niewyrównane, tak aby nowe wiadomości lub fragmentem musiałaby krzyżowego względem innych. Objawy może być, że odbywa się bez zmian lub zostanie zgłoszony wyjątek. Wyjątek nie może zostać zgłoszone do momentu `UpdateShapePositions()` lub `Layout()` operacja została wykonana.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>   
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)



