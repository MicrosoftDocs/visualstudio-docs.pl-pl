---
title: Projektant przepływu pracy — Projektant działań TerminateWorkflow
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01003005e9f73138e5a430b21e538c5c241e7f9f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649880"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow, projektant działań

Projektant działań **TerminateWorkflow** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.TerminateWorkflow>.

## <a name="the-terminateworkflow-activity"></a>Działanie TerminateWorkflow

Działanie <xref:System.Activities.Statements.TerminateWorkflow> kończy wykonywanie przepływu pracy.

### <a name="using-the-terminateworkflow-activity-designer"></a>Korzystanie z projektanta działań TerminateWorkflow

Projektanta działań **TerminateWorkflow** można znaleźć w kategorii **środowiska uruchomieniowego** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** (można również wybrać **Przybornik** z menu **Widok** lub Ctrl + Alt + X.)

Projektanta działań **TerminateWorkflow** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.TerminateWorkflow> z domyślną wartością **DisplayName** TerminateWorkflow. @No__t_0 można edytować w nagłówku projektanta działań **TerminateWorkflow** lub w polu **DisplayName** siatki właściwości.

### <a name="the-terminateworkflow-properties"></a>Właściwości TerminateWorkflow

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.TerminateWorkflow> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.TerminateWorkflow>. Wartość domyślna to TerminateWorkflow. Chociaż nazwa wyświetlana nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie nazwy wyświetlanej.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Wyjątek, który należy zgłosić po zakończeniu przepływu pracy. Ustaw tę właściwość w siatce właściwości.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Powód, który wyjaśnia, dlaczego przepływ pracy został zakończony. Ustaw tę właściwość w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Środowisko uruchomieniowe](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)