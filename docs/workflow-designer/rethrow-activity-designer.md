---
title: Projektant przepływu pracy — Zgłoś ponownie projektanta działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 558ff5a36d172b8cd1fef0b811d1eaa920b90c6d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009278"
---
# <a name="rethrow-activity-designer"></a>Rethrow, projektant działań

**Zgłoś ponownie** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Rethrow> działania.

## <a name="the-rethrow-activity"></a>Działanie ponownego zgłoszenia

<xref:System.Activities.Statements.Rethrow> Działanie zgłasza wcześniej zgłoszony wyjątek. To działanie można używać tylko w <xref:System.Activities.Statements.Catch> obsługi w <xref:System.Activities.Statements.TryCatch> działania.

### <a name="use-the-rethrow-activity-designer"></a>Za pomocą projektanta działań Zgłoś ponownie

Dostęp do **Zgłoś ponownie** projektanta działań w **obsługę błędów** kategorii **przybornika**. **Zgłoś ponownie** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.Rethrow> działanie przy użyciu domyślnego **DisplayName** z Throw. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **Zgłoś ponownie** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-rethrow-properties"></a>Zgłoś ponownie właściwości

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Rethrow> właściwości, a w tym artykule opisano, jak są używane w Projektancie:

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalny przyjazna nazwa <xref:System.Activities.Statements.Rethrow> działania. Wartość domyślna to Zgłoś ponownie.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)