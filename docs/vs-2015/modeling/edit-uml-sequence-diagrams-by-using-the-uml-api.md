---
title: Edytowanie diagramów sekwencji UML przy użyciu interfejsu API UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbc7a6ce7edede6759c0562df1e524d932f62b91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669713"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>Edytowanie diagramów sekwencji UML przy użyciu interfejsu API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interakcja to sekwencja komunikatów między zestawem linii życia. Interakcja jest wyświetlana na diagramie sekwencji UML.

 Aby uzyskać szczegółowe informacje o interfejsie API, zobacz [Microsoft. VisualStudio. UML.](/previous-versions/dd493373(v=vs.140))Interactions.

 Aby zapoznać się z bardziej ogólnym wprowadzeniem do pisania poleceń i obsługi gestów dla diagramów UML, zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

## <a name="basic-code"></a>Kod podstawowy

### <a name="namespace-imports"></a>Importy przestrzeni nazw
 Należy uwzględnić następujące `using` instrukcje:

```
using Microsoft.VisualStudio.Uml.Classes;
   // for basic UML types such as IPackage
using Microsoft.VisualStudio.Uml.Interactions;
   // for interaction types
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   // to create elements and use additional functions
```

 W przypadku tworzenia poleceń menu i programów obsługi gestów potrzebne są również następujące elementy:

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
 Jeśli edytujesz interakcję jako część obsługi polecenia lub gestu w diagramie sekwencji, możesz uzyskać odwołanie do kontekstu. Na przykład:

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

### <a name="generated-and-uml-sequence-diagrams"></a>Generowane diagramy sekwencji UML
 Istnieją dwa rodzaje diagramów sekwencji: te, które są tworzone ręcznie w projekcie modelowania UML, oraz te, które zostały wygenerowane na podstawie kodu programu. Użyj `UmlMode` właściwości, aby odnaleźć diagram sekwencji.

> [!NOTE]
> Ta właściwość zwraca wartość false tylko dla diagramów sekwencji generowanych na podstawie kodu przy użyciu Visual Studio 2013 i wcześniejszych. Obejmuje to diagramy sekwencji wygenerowane przez kod z 2013 i wcześniejszych. Ta wersja programu Visual Studio nie obsługuje generowania nowych diagramów sekwencji.

 Na przykład jeśli chcesz wykonać polecenie menu, które jest widoczne tylko w diagramach sekwencji UML, `QueryStatus()` Metoda może zawierać następującą instrukcję:

```
command.Enabled = command.Visible =
      sequenceDiagram != null && sequenceDiagram.UmlMode;
```

 Na wygenerowanym diagramie sekwencji linie życia, wiadomości i inne elementy są w większości takie same jak na diagramie sekwencji UML. W modelu UML Magazyn modeli ma główny model, który jest właścicielem wszystkich innych elementów. Jednak wygenerowana interakcja istnieje w swoim własnym magazynie modeli, która ma korzeń o wartości null:

```
IModel rootModel = sequenceDiagram.ModelStore.Root;
    // !sequenceDiagram.UmlMode == (rootModel == null)
```

## <a name="to-create-and-display-an-interaction"></a>Aby utworzyć i wyświetlić interakcję
 Utwórz interakcję jako element podrzędny pakietu lub modelu.

 Na przykład, Jeśli opracowujesz polecenie, które może być wykonane na pustym diagramie sekwencji, zawsze należy zacząć od sprawdzenia, czy interakcja istnieje.

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

## <a name="updating-an-interaction-and-its-layout"></a>Aktualizowanie interakcji i jej układu
 Podczas aktualizowania interakcji należy zawsze zakończyć operację przez aktualizację układu przy użyciu jednej z następujących metod:

- `ISequenceDiagram.UpdateShapePositions()` dostosowuje położenie kształtów, które zostały ostatnio wstawione lub przeniesione, oraz ich sąsiednich kształtów.

- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` Odświeża cały diagram. Można użyć parametru, aby określić zmiany położenia linii życia, wiadomości lub obu tych elementów.

  Jest to szczególnie ważne podczas wstawiania nowych elementów lub przenoszenia istniejących elementów. Nie będą znajdować się w poprawnych położeniach na diagramie, dopóki nie zostanie wykonana jedna z tych operacji. Wystarczy tylko wywołać jedną z tych operacji na końcu serii zmian.

  Aby uniknąć bemusing przez użytkownika, który wykonuje cofnięcie po poleceniu, użyj polecenia, `ILinkedUndoTransaction` aby zawrzeć zmiany i ostateczne `Layout()` lub `UpdateShapePositions()` operacje. Na przykład:

```
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))
{
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);
  Diagram.UpdateShapePositions();
  transaction.Commit();
}
```

 Aby użyć `ILinkedUndoTransaction` , należy wprowadzić tę deklarację w swojej klasie:

```
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }
```

 Aby uzyskać więcej informacji, zobacz [łączenie aktualizacji modelu UML przy użyciu transakcji](../modeling/link-uml-model-updates-by-using-transactions.md).

## <a name="building-an-interaction"></a>Tworzenie interakcji

### <a name="to-create-lifelines"></a>Aby utworzyć linie życia

```
ILifeline lifeline = interaction.CreateLifeline();
```

 Linia życia reprezentuje element, który można podłączyć, czyli wystąpienie typu. Na przykład, jeśli interakcja służy do pokazywania, w jaki sposób składnik deleguje przychodzące komunikaty do jego części wewnętrznych, linie życia mogą reprezentować porty i części składnika:

```
foreach (IConnectableElement part in
            component.Parts
           .Concat<IConnectableElement>(component.OwnedPorts))
{
   ILifeline lifeline = interaction.CreateLifeline();
   lifeline.Represents = part;
}
```

 Alternatywnie, jeśli interakcja zawiera dowolny zestaw obiektów, można utworzyć właściwość lub inną `IConnectableElement` interakcję:

```
ILifeline lifeline = interaction.CreateLifeline();
IProperty property1 = interaction.CreateProperty();
property1.Type = model.CreateInterface();
property1.Type.Name = "Type 1";
lifeline.Represents = property1;
```

 Alternatywnie można ustawić nazwę i typ linii życia bez łączenia jej z elementem łączącym:

```
ILifeline lifeline = interaction.CreateLifeline();
lifeline.Name = "c1";
lifeline.SetInstanceType("Customer");
System.Diagnostics.Debug.Assert(
           lifeline.GetDisplayName() == "c1:Customer"  );
```

### <a name="to-create-messages"></a>Aby utworzyć komunikaty
 Aby utworzyć komunikat, należy zidentyfikować punkty wstawiania w źródłowej i docelowej linii życia. Na przykład:

```
interaction.CreateMessage( sourceInsertionPoint,
                           targetInsertionPoint,
                           MessageKind.Complete,
                           MessageSort.ASynchCall)
```

 Aby utworzyć komunikat z niezdefiniowanym źródłem lub niezdefiniowanym obiektem docelowym:

```
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);
```

 Istnieje kilka komunikatów, za pomocą których można identyfikować punkty wstawiania we wszystkich kluczowych punktach linii życia:

|Metoda w ILifeline|Użyj jej do wstawienia w tym momencie|
|-------------------------|------------------------------------|
|`FindInsertionPointAtTop()`|Góra linii życia.|
|`FindInsertionPointAtBottom()`|Dolna część linii życia.|
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Punkt natychmiast po określonym komunikacie.|
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|Punkt może być w linii życia lub w bloku specyfikacji wykonywania nadrzędnego.|
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Punkt po użyciu interakcji.|
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Punkt po połączonym fragmencie.|
|`FindInsertionPoint(IExecutionSpecification block)`|Góra bloku wykonywania.|
|`FindInsertionPoint(IInteractionOperand fragment)`|Góra operandu połączonego fragmentu.|

 Podczas tworzenia komunikatów należy zachować ostrożność, aby uniknąć definiowania komunikatu, który mógłby przekroczyć inny komunikat.

### <a name="to-create-combined-fragments-and-interaction-uses"></a>Aby utworzyć połączone fragmenty i użycie interakcji
 Połączone fragmenty i sposoby interakcji można tworzyć, określając punkt wstawiania dla każdej linii życia, która musi być objęta przez element. Należy unikać określania zestawu punktów, które przechodzą przez istniejący komunikat lub fragment.

```
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));
Interaction.CreateInteractionUse(
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));
```

 Można również utworzyć połączony fragment obejmujący istniejący zestaw komunikatów. Wszystkie komunikaty muszą być źródła w tym samym bloku linii życia lub wykonania.

```
ICombinedFragment cf = Interaction.CreateCombinedFragment(
  InteractionOperatorKind.Loop,
  Interaction.Lifelines.First().GetAllOutgoingMessages());
```

 Połączony fragment jest zawsze tworzony z pojedynczym argumentem operacji. Aby utworzyć nowy operand, należy określić istniejący operand, który ma zostać wstawiony przed lub po, oraz czy chcesz wstawić po nim lub przed nim:

```
// Create an additional operand before the first
cf.CreateInteractionOperand(cf.Operands.First(), false);
// Create an additional operand after the last:
cf.CreateInteractionOperand(cf.Operands.Last(), true);
```

## <a name="troubleshooting"></a>Rozwiązywanie problemów
 Kształty będą wyświetlane w niepoprawnych położeniach, jeśli zmiany nie zostaną zakończone `UpdateShapePositions()` `Layout()` operacją lub.

 Większość innych problemów jest spowodowanych przez niewyrównane punkty wstawiania, dzięki czemu nowe komunikaty lub fragmenty będą musiały przekroczyć inne elementy. Objawy mogą polegać na tym, że zmiany nie są wykonywane lub wyjątek jest zgłaszany. Wyjątek może nie być zgłaszany do momentu `UpdateShapePositions()` `Layout()` wykonania operacji lub.

## <a name="see-also"></a>Zobacz też

- [Microsoft. VisualStudio. UML. Interactions](/previous-versions/dd493373(v=vs.140))
- [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)
- [Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
- [Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md)
- [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)
- [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)
