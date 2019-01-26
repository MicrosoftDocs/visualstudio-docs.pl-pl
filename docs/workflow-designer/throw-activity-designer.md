---
title: Projektant przepływu pracy — Throw, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60b7396c8a57b6ddcf9ea48c04a17f070194ccdc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940521"
---
# <a name="throw-activity-designer"></a>Throw, projektant działań

**Throw** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Throw> działania.

## <a name="the-throw-activity"></a>Działanie Throw

<xref:System.Activities.Statements.Throw> Działanie zgłasza wyjątek.

### <a name="using-the-throw-activity-designer"></a>Za pomocą projektanta działań Throw

Dostęp do **Throw** projektanta działań w **obsługę błędów** kategorii **przybornika**.

**Throw** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Throw> działanie przy użyciu domyślnego **DisplayName** z Throw. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **Throw** projektanta działań lub **DisplayName** pola siatki właściwości. <xref:System.Activities.Statements.Throw.Exception%2A> Można edytować właściwości, w siatce właściwości.

### <a name="the-throw-properties"></a>Właściwości Throw

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Throw> właściwości i w tym artykule opisano, jak są używane w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalny przyjazna nazwa <xref:System.Activities.Statements.Throw> działania. Wartość domyślna to Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Prawda|Wyjątek do zgłoszenia. Ten wyjątek musi pochodzić od klasy <xref:System.Exception>. Aby określić wyjątek, wpisz wyrażenie języka Visual Basic w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw, projektant działań](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)