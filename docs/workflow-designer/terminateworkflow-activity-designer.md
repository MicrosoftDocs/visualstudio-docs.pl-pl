---
title: Projektant przepływu pracy — TerminateWorkflow, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8dc6328e2363e802d05093bfebd25479d67c6ffa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858503"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow, projektant działań

**TerminateWorkflow** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.TerminateWorkflow> działania.

## <a name="the-terminateworkflow-activity"></a>Działanie TerminateWorkflow

<xref:System.Activities.Statements.TerminateWorkflow> Działanie kończy wykonywanie przepływu pracy.

### <a name="using-the-terminateworkflow-activity-designer"></a>Za pomocą TerminateWorkflow, Projektant działań

**TerminateWorkflow** projektanta działań można znaleźć w **środowiska uruchomieniowego** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** karty (opcjonalnie zaznacz **przybornika** z **widoku** menu lub klawiszy CTRL + ALT + X.)

**TerminateWorkflow** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.TerminateWorkflow> działanie przy użyciu domyślnego **DisplayName** z TerminateWorkflow. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **TerminateWorkflow** projektanta działań lub **DisplayName** pola siatki właściwości.

### <a name="the-terminateworkflow-properties"></a>Właściwości TerminateWorkflow

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.TerminateWorkflow> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich mogą być edytowane na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.TerminateWorkflow> działania. Wartość domyślna to TerminateWorkflow. Chociaż nazwa wyświetlana nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć nazwy wyświetlanej.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Wyjątek do zgłaszania, gdy przepływ pracy zostanie zakończony. Ustaw tę właściwość w siatce właściwości.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Powód, który wyjaśnia, dlaczego przepływu pracy zostało zakończone. Ustaw tę właściwość w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Środowisko uruchomieniowe](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)