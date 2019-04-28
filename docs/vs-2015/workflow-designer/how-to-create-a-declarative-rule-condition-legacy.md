---
title: 'Instrukcje: Tworzenie warunku reguły deklaratywnej (starsza wersja) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dbdcc268b71f2926307b500126840391dd5308fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931245"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Instrukcje: Tworzenie warunku reguły deklaratywnej (starsza wersja)
W tym temacie opisano sposób deklarowania warunku reguły, za pomocą starszego [!INCLUDE[wfd1](../includes/wfd1-md.md)] przeznaczonego [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Instrukcja warunku daje w wyniku **True** lub **False**. Warunku reguły deklaratywnej jest instrukcja warunku, który jest tworzony przy użyciu [(starsza wersja) okno dialogowe Edytor warunku reguły](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) i przechowywane jako XML z przepływem pracy. Może obejmować predykatów, pozwalające porównać stanu przepływu pracy i algebry atrybut typu wartość logiczna, łączącą wielu predykatów.  
  
 Warunki reguły deklaratywnej są używane w następujących działaniach out-of-box Windows Workflow Foundation:  
  
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Aby utworzyć warunku reguły deklaratywnej przy użyciu Edytor warunku reguły  
  
1. W ramach działania **właściwości** okna, kliknij przycisk **warunek** właściwości lub **UntilCondition** właściwości, w zależności od działania.  
  
2. Wybierz **deklaratywne warunku reguły** z listy właściwości.  
  
3. Rozwiń **warunek** lub **UntilCondition** właściwości.  
  
4. Kliknij przycisk **ConditionName** właściwości.  
  
5. Kliknij przycisk **ConditionName** wielokropek **[...]**  otworzyć **wybierz warunek** okno dialogowe.  
  
6. Kliknij przycisk **nowy warunek** otworzyć **Edytor warunku reguły** okno dialogowe.  
  
7. Wpisz wyrażenie dla warunku w **warunek** pola tekstowego.  
  
     Aby uzyskać informacje o sposobie tworzenia wyrażenia warunku, zobacz [(starsza wersja) okno dialogowe Edytor warunku reguły](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8. Po zakończeniu tworzenia wyrażenia warunku kliknij **OK** aby zamknąć okno dialogowe i utworzyć warunek reguły z przypisaną nazwę.  
  
     **Wybierz warunek** zostanie otwarte okno dialogowe.  
  
     Aby uzyskać informacje o sposobie używania **wybierz warunek** okno dialogowe, zobacz [wybierz warunek okno dialogowe (starsza wersja)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)   
 [Za pomocą grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Przy użyciu działania IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Przy użyciu działania replikatora](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Za pomocą While działania](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Okno dialogowe Edytor warunku reguły (starsza wersja)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Wybieranie warunku, okno dialogowe (starsza wersja)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Za pomocą warunków w przepływach pracy](http://go.microsoft.com/fwlink?LinkID=65009)