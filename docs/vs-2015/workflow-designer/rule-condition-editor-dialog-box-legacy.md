---
title: Edytor warunku reguły — okno dialogowe (starsza wersja) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 93aef1e4466bd88d87ebce71161dcd1665178317
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663352"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Edytor warunku reguły, okno dialogowe (starsza wersja)
W tym temacie opisano sposób użycia okna dialogowego **Edytor warunku reguły** w starszej [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszej [!INCLUDE[wfd2](../includes/wfd2-md.md)], jeśli chcesz wskazać [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Można tworzyć i modyfikować warunki reguły deklaracyjnej przy użyciu okna dialogowego **Edytor warunku reguły** . Te warunki reguły są udostępniane jako właściwości w następujących Windows Workflow Foundation działaniach gotowych:

- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

- [Działanie ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

- [While](http://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

  Dostęp do okna dialogowego **Edytor warunku reguły** można uzyskać, korzystając z [okna dialogowego Wybieranie warunku (starsza wersja)](../workflow-designer/select-condition-dialog-box-legacy.md).

  W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Edytor warunku reguły** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Rozgrzewa**|Wprowadź wyrażenie dla warunku reguły.|
|**Ok**|Kliknij, aby zapisać warunek reguły.|

## <a name="entering-condition-expressions"></a>Wprowadzanie wyrażeń warunku
 Wyrażenia warunku są wprowadzane jako tekst. Możesz to wpisać **.** do edytora, aby odwoływać się do pól, właściwości i metod używanych w przepływie pracy przy użyciu menu IntelliSense. Lub można wpisać bezpośrednio nazwę elementu członkowskiego przepływu pracy. Można dodać operatory logiczne do warunku, takie jak i, lub, i nie. Można również dodać predykaty. Predykat jest operatorem binarnym i dwoma operandami. Obsługiwane operatory binarne to **==** , **>** , **\<** , **>=** i **<=** . Obsługiwane argumenty operacji to stała wartość, funkcja arytmetyczna i publiczne elementy członkowskie z zakresem.

 Można określić typ porównania i można ją porównać z **wartością null** lub ciągiem pustym. Można wykonywać zagnieżdżone wywołania do elementów członkowskich na zmiennej, która zawiera typ złożony, na przykład `this.Address.State == "WA"`.

 Edytor warunku reguły obsługuje następujące operatory:

- Operatory relacyjne: = =, =,! =

- Operatory porównania: <, \< =, >, > =

- Operatory arytmetyczne: +,-, *,/, MOD

- Operatory logiczne: i, & &, lub, &#124; &#124;, nie,!

- Operatory bitowe: &,&#124;

  Pierwszeństwo operatorów wyrażeń C# następuje po regułach pierwszeństwa operatorów.

  Edytor warunku reguły obsługuje następujące wyrażenia liczbowe:

  this. i = 1D (jest to rozwiązywane do 1,0)

  this. i = = 1E1 (jest to rozwiązywane do 10,0)

  this. i = = 1L (jako Long)

  Ta wartość. i = = 1M (jest rozpoznawana jako liczba dziesiętna)

  this. i = = 1F (jest rozpoznawany jako pojedynczy)

  this. i = = 1U (jest rozpoznawana jako liczba całkowita bez znaku)

  Aby uzyskać więcej informacji o warunkach, zobacz [Używanie warunków w przepływach pracy](http://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Zobacz też
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033) [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) [](http://go.microsoft.com/fwlink?LinkID=65039) [](http://go.microsoft.com/fwlink?LinkID=65049) — [okno dialogowe wyboru stanu (starsza wersja)](../workflow-designer/select-condition-dialog-box-legacy.md) [w przypadku przepływów](http://go.microsoft.com/fwlink?LinkID=65009) pracy [starszy projektant programu Windows Workflow Pomoc interfejsu użytkownika Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)