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
ms.openlocfilehash: a632b90e89e58c26ec72083fe3f4ed9223826dae
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302844"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Edytor warunku reguły, okno dialogowe (starsza wersja)
W tym temacie opisano sposób użycia okna dialogowego **Edytor warunku reguły** w starszej [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszego [!INCLUDE[wfd2](../includes/wfd2-md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Można tworzyć i modyfikować warunki reguły deklaracyjnej przy użyciu okna dialogowego **Edytor warunku reguły** . Te warunki reguły są udostępniane jako właściwości w następujących Windows Workflow Foundation działaniach gotowych:

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [Działanie ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

  Dostęp do okna dialogowego **Edytor warunku reguły** można uzyskać, korzystając z [okna dialogowego Wybieranie warunku (starsza wersja)](../workflow-designer/select-condition-dialog-box-legacy.md).

  W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Edytor warunku reguły** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Rozgrzewa**|Wprowadź wyrażenie dla warunku reguły.|
|**OK**|Kliknij, aby zapisać warunek reguły.|

## <a name="entering-condition-expressions"></a>Wprowadzanie wyrażeń warunku
 Wyrażenia warunku są wprowadzane jako tekst. Możesz to wpisać **.** do edytora, aby odwoływać się do pól, właściwości i metod używanych w przepływie pracy przy użyciu menu IntelliSense. Lub można wpisać bezpośrednio nazwę elementu członkowskiego przepływu pracy. Można dodać operatory logiczne do warunku, takie jak i, lub, i nie. Można również dodać predykaty. Predykat jest operatorem binarnym i dwoma operandami. Obsługiwane operatory binarne to **==** , **>** , **\<** , **>=** i **<=** . Obsługiwane argumenty operacji to stała wartość, funkcja arytmetyczna i publiczne elementy członkowskie z zakresem.

 Można określić typ porównania i można ją porównać z **wartością null** lub ciągiem pustym. Można wykonywać zagnieżdżone wywołania do elementów członkowskich na zmiennej, która zawiera typ złożony, na przykład `this.Address.State == "WA"`.

 Edytor warunku reguły obsługuje następujące operatory:

- Operatory relacyjne: = =, =,! =

- Operatory porównania: <, \<=, >, > =

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

  Aby uzyskać więcej informacji o warunkach, zobacz [Używanie warunków w przepływach pracy](https://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Zobacz też
 [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033) [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) [](https://go.microsoft.com/fwlink?LinkID=65039) [](https://go.microsoft.com/fwlink?LinkID=65049) — [okno dialogowe wyboru stanu (starsza wersja)](../workflow-designer/select-condition-dialog-box-legacy.md) [użycie warunków w obszarze przepływy pracy](https://go.microsoft.com/fwlink?LinkID=65009) [starszego projektanta dla pomocy interfejsu użytkownika Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)