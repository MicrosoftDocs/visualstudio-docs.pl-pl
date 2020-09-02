---
title: Okno dialogowe Wybieranie warunku (starsza wersja) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.ConditionBrowserDialog.UI
helpviewer_keywords:
- Select Condition dialog box
ms.assetid: fe3b415c-cb55-4295-b853-3f40765b28d0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bece06c618e5fcc0e91dcbd683b961979fd76dcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846193"
---
# <a name="select-condition-dialog-box-legacy"></a>Wybieranie warunku, okno dialogowe (starsza wersja)
W tym temacie opisano sposób użycia okna dialogowego **Wybierz warunek** w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Użyj starszej wersji, [!INCLUDE[wfd2](../includes/wfd2-md.md)] gdy musisz być celem [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Okno dialogowe **Wybieranie warunku** służy do wybierania warunku reguły deklaratywnej, która ma zostać przypisana do właściwości warunku działania. Te warunki reguły są udostępniane jako właściwości w następujących Windows Workflow Foundation działaniach gotowych:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [Działanie ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [While](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

  Aby uzyskać informacje o tym, jak uzyskać dostęp do okna dialogowego **Wybierz warunek** , zobacz [How to: Create a deklaratywn Rule Condition (starsza wersja)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md).

  W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Wybieranie warunku** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Nowy...**|Kliknij, aby otworzyć okno [dialogowe Edytor warunku reguły (starsza wersja)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) , aby utworzyć nowy warunek reguły.|
|**Edytuj...**|Kliknij, aby otworzyć okno [dialogowe Edytor warunku reguły (starsza wersja)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) , aby edytować wybrany warunek reguły.|
|**Zmień nazwę...**|Kliknij, aby otworzyć okno dialogowe używane do zmiany nazwy wybranego warunku reguły.|
|**Usuń**|Kliknij, aby usunąć wybrany warunek reguły.|
|**Podgląd warunku**|Wyświetla wyrażenie warunku dla wybranego warunku reguły.|
|**OK**|Kliknij, aby przypisać wybrany warunek reguły do warunku działania.|

 Aby uzyskać więcej informacji na temat tworzenia i edytowania warunków reguł, zobacz [okno dialogowe Edytor warunku reguły (starsza wersja)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

 Aby uzyskać więcej informacji o warunkach, zobacz [Używanie warunków w przepływach pracy](https://msdn2.microsoft.com/library/bb628447.aspx).

## <a name="see-also"></a>Zobacz też
 [Edytor warunku reguły — okno dialogowe (starsza wersja)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [instrukcje: Tworzenie warunku reguły deklaratywnej (starsza wersja)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) [przy użyciu warunków w przepływach pracy](https://msdn2.microsoft.com/library/bb628447.aspx) [przy użyciu działania ConditionedActivityGroup](https://msdn2.microsoft.com/library/bb675237.aspx) [za pomocą działania IfElseBranchActivity](https://msdn2.microsoft.com/library/bb628465.aspx) [przy użyciu działania Replikator](https://msdn2.microsoft.com/library/bb628544.aspx) [przy użyciu funkcji while](https://msdn2.microsoft.com/library/bb628552.aspx) [starszej wersji narzędzia dla Windows Workflow Foundation interfejsu użytkownika](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)
