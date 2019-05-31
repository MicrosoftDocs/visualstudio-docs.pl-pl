---
title: Okno dialogowe Edytor warunku reguły (starsza wersja) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8237c8e29007d010cd99e4323bf8e88a23b7e9fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006830"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Edytor warunku reguły, okno dialogowe (starsza wersja)
W tym temacie opisano sposób użycia **Edytor warunku reguły** okno dialogowe w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszego [!INCLUDE[wfd2](../includes/wfd2-md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Tworzenie i modyfikowanie warunki reguły deklaratywnej za pomocą **Edytor warunku reguły** okno dialogowe. Te warunki reguły są widoczne jako właściwości na następujących działaniach out-of-box Windows Workflow Foundation:  
  
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
  Możesz uzyskać dostęp do **Edytor warunku reguły** okno dialogowe, za pomocą [wybierz warunek okno dialogowe (starsza wersja)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
  W poniższej tabeli opisano elementy interfejsu użytkownika **Edytor warunku reguły** okno dialogowe.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Warunek:**|Wprowadź wyrażenie dla warunku reguły.|  
|**OK**|Kliknij, aby zapisać warunek reguły.|  
  
## <a name="entering-condition-expressions"></a>Wprowadzanie wyrażenia warunku  
 Warunek wyrażenia są wprowadzane jako tekst. Możesz wpisać **to.** do edytora, aby odwoływać się do pola, właściwości i metody używane w przepływie pracy przy użyciu menu podobne do funkcji IntelliSense. Lub możesz bezpośrednio wpisać nazwę elementu członkowskiego przepływu pracy. Operatory logiczne można dodać do warunku, takich jak AND, OR i NOT. Można również dodać predykatów. Predykat jest operator binarny i dwóch argumentów operacji. Operatory dwuargumentowe, obsługiwane są **==** , **>** , **\<** , **>=** , i **<=** . Obsługiwane argumenty operacji są wartości stałej, funkcja arytmetyczne i zakresie publiczne elementy członkowskie.  
  
 Można określić typ porównania i możesz porównać **null** ani być pustym ciągiem. Można wprowadzić zagnieżdżone wywołania do elementów członkowskich na zmienną, która zawiera typ złożony, na przykład `this.Address.State == "WA"`.  
  
 Edytor warunku reguły obsługuje następujące operatory:  
  
- Operatory relacyjne: ==, =,! =  
  
- Operatory porównania: <, \<=, >, > =  
  
- Operatory arytmetyczne: +, -, *, / MOD  
  
- Operatory logiczne: PONADTO &AMP; &AMP;, OR &AMP;#124; &AMP;#124;, NIE!  
  
- Bitwise operators: &, &#124;  
  
  Kolejność wykonywania wyrażenia następuje reguły pierwszeństwa operatorów języka C#.  
  
  Edytor warunku reguły obsługuje następujące wyrażenia liczbowego:  
  
  this.i == 1D (rozwiązuje 1.0)  
  
  this.i == 1E1 (jest rozpoznawana jako 10.0)  
  
  this.i == 1L (rozwiązuje jako wartość długa)  
  
  this.i == 1 mln (rozwiązuje jako ułamek dziesiętny)  
  
  this.i == 1F (jest rozpoznawana jako pojedynczy)  
  
  this.i == 1U (jest rozpoznawana jako unsigned int)  
  
  Aby uzyskać więcej informacji o warunkach, zobacz [za pomocą warunków w przepływach pracy](http://go.microsoft.com/fwlink?LinkID=65009).  
  
## <a name="see-also"></a>Zobacz też  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [Działanie WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Wybieranie warunku, okno dialogowe (starsza wersja)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Za pomocą warunków w przepływach pracy](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Starsza wersja projektanta pomocy interfejsu użytkownika programu Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)