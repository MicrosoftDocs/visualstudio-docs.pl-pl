---
title: Projektant przepływu pracy — Persist, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c97d916d00d1c976b4e27381f55e42cbb7cb0db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004122"
---
# <a name="persist-activity-designer"></a>Persist, projektant działań

**Utrwalanie** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Persist> działania.

## <a name="the-persist-activity"></a>Utrwalanie działania

<xref:System.Activities.Statements.Persist> Działanie zapisuje przepływ pracy na dysku, jeśli jest to możliwe. <xref:System.Activities.Statements.Persist> Działania nie można wykonać w strefie bez trwałości, jak na przykład w ramach <xref:System.Activities.Statements.TransactionScope> działania. Jeśli używasz <xref:System.Activities.Statements.Persist> działań w zakresie bez trwałości, zgłaszany jest wyjątek w czasie wykonywania.

### <a name="using-the-persist-activity-designer"></a>Za pomocą Persist, Projektant działań

**Utrwalanie** projektanta działań można znaleźć w **środowiska uruchomieniowego** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** Karta (można także wybrać **przybornika** z **widoku** menu lub klawiszy CTRL + ALT + X.)

**Utrwalanie** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Persist> działanie przy użyciu domyślnego **DisplayName** z utrwalanie. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **utrwalanie** projektanta działań lub **DisplayName** pola siatki właściwości.

### <a name="the-persist-properties"></a>Utrwalanie właściwości

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Persist> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich mogą być edytowane na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Persist> działania. Wartość domyślna to utrwalanie. Chociaż nazwa wyświetlana nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć nazwy wyświetlanej.|

## <a name="see-also"></a>Zobacz także

- [Środowisko uruchomieniowe](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)