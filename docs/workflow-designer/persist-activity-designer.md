---
title: Projektant przepływu pracy — Projektant działań utrwalania
description: Dowiedz się więcej o działaniu utrwalania i sposobach tworzenia i konfigurowania działania utrwalania przy użyciu projektanta działań trwałych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 988c080b7b6c89baa4151858fcaf4e3320582e09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968726"
---
# <a name="persist-activity-designer"></a>Persist, projektant działań

Projektant działań **utrwalania** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Persist> działania.

## <a name="the-persist-activity"></a>Działanie utrwalania

<xref:System.Activities.Statements.Persist>Działanie zapisuje przepływ pracy na dysku, jeśli jest to możliwe. <xref:System.Activities.Statements.Persist>Działanie nie może zostać wykonane w strefie nietrwałości, jak na przykład w ramach <xref:System.Activities.Statements.TransactionScope> działania. Jeśli używasz <xref:System.Activities.Statements.Persist> działania w zakresie nietrwałości, wyjątek jest zgłaszany w czasie wykonywania.

### <a name="using-the-persist-activity-designer"></a>Korzystanie z projektanta działań utrwalania

Projektanta działań **utrwalania** można znaleźć w kategorii **środowiska uruchomieniowego** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** (można również wybrać **Przybornik** z menu **Widok** lub CTRL + ALT + X).

Projektanta działań **utrwalania** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.Persist> działania z domyślną wartością **DisplayName** elementu utrwalania. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **trwałych** lub w polu **DisplayName** siatki właściwości.

### <a name="the-persist-properties"></a>Właściwości utrwalania

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Persist> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.Persist> działania. Wartość domyślna to utrwalanie. Chociaż nazwa wyświetlana nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie nazwy wyświetlanej.|

## <a name="see-also"></a>Zobacz też

- [Środowisko uruchomieniowe](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
