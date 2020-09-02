---
title: 'Instrukcje: Tworzenie warunku reguły deklaratywnej (starsza wersja) | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c23fed64d7f3a7681fce96663262f6d633299a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849333"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Instrukcje: Tworzenie warunku reguły deklaratywnej (starsza wersja)
W tym temacie opisano, jak zadeklarować warunek reguły przy użyciu starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] , która jest przeznaczona dla [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Instrukcja warunku daje w wyniku **wartość true** lub **false**. Warunek reguły deklaratywnej jest instrukcją warunkową, która jest tworzona przy użyciu [okna dialogowego Edytor warunku reguły (starsza wersja)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) i przechowywana jako plik XML z przepływem pracy. Może obejmować predykaty, które porównują stan przepływu pracy i wartość logiczną algebry, która łączy wiele predykatów.

 Warunki reguły deklaracyjnej są używane w następujących Windows Workflow Foundation działaniach poza ramką:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [Działanie ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [While](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Aby utworzyć warunek reguły deklaracyjnej przy użyciu edytora warunków reguły

1. W oknie **Właściwości** działania kliknij właściwość **warunek** lub właściwość **UntilCondition** , w zależności od działania.

2. Wybierz z listy Właściwość **warunek reguły deklaratywnej** .

3. Rozwiń **warunek** lub właściwość **UntilCondition** .

4. Kliknij właściwość **ConditionName** .

5. Kliknij wielokropek **[...]** **, aby** otworzyć okno dialogowe **Wybieranie warunku** .

6. Kliknij przycisk **Nowy warunek** , aby otworzyć okno dialogowe **Edytor warunku reguły** .

7. Wpisz wyrażenie dla warunku w polu tekstowym **warunek** .

     Aby uzyskać informacje o sposobach tworzenia wyrażeń warunkowych, zobacz [okno dialogowe Edytor warunku reguły (starsza wersja)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Po zakończeniu tworzenia wyrażenia warunku kliknij przycisk **OK** , aby zamknąć okno dialogowe i utworzyć warunek reguły z przypisaną nazwą.

     Zostanie otwarte okno dialogowe **Wybieranie warunku** .

     Aby uzyskać informacje o sposobach korzystania z okna dialogowego **Wybierz warunek** , zobacz [okno dialogowe Wybieranie warunku (starsza wersja)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Zobacz też
 [Działania ze starszych przepływów pracy](../workflow-designer/legacy-workflow-activities.md) [przy użyciu ConditionedActivityGroup](https://msdn2.microsoft.com/library/bb675237.aspx) [przy użyciu działania IfElseBranchActivity](https://msdn2.microsoft.com/library/bb628465.aspx) [przy użyciu działania Replikator](https://msdn2.microsoft.com/library/bb628544.aspx) [przy użyciu](https://msdn2.microsoft.com/library/bb628552.aspx) okna [dialogowego Edytor warunku reguły działania okno dialogowe (starsze)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) okno dialogowe [Wybieranie warunku (starsze)](../workflow-designer/select-condition-dialog-box-legacy.md) [użycie warunków w przepływach pracy](https://msdn2.microsoft.com/library/bb628447.aspx)
