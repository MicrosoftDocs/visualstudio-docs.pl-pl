---
title: Projektant przepływu pracy — Projektant działań utrwalania
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75236d7955cba6b8c62b9a4504f02c66cebe4062
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114766"
---
# <a name="persist-activity-designer"></a>Persist, projektant działań

Projektant działań **utrwalania** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.Persist>.

## <a name="the-persist-activity"></a>Działanie utrwalania

Działanie <xref:System.Activities.Statements.Persist> zapisuje przepływ pracy na dysku, jeśli jest to możliwe. Działanie <xref:System.Activities.Statements.Persist> nie może zostać wykonane w strefie nietrwałości, tak jak na przykład w działaniu <xref:System.Activities.Statements.TransactionScope>. Jeśli używasz działania <xref:System.Activities.Statements.Persist> w zakresie nietrwałości, wyjątek jest zgłaszany w czasie wykonywania.

### <a name="using-the-persist-activity-designer"></a>Korzystanie z projektanta działań utrwalania

Projektanta działań **utrwalania** można znaleźć w kategorii **środowiska uruchomieniowego** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** (można również wybrać **Przybornik** z menu **Widok** lub CTRL + ALT + X).

Projektanta działań **utrwalania** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.Persist> z domyślną wartością **DisplayName** elementu utrwalania. <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **trwałych** lub w polu **DisplayName** siatki właściwości.

### <a name="the-persist-properties"></a>Właściwości utrwalania

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Persist> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa działania <xref:System.Activities.Statements.Persist>. Wartość domyślna to utrwalanie. Chociaż nazwa wyświetlana nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie nazwy wyświetlanej.|

## <a name="see-also"></a>Zobacz także

- [Środowisko uruchomieniowe](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
