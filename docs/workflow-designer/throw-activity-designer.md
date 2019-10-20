---
title: Projektant przepływu pracy-throw — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe6a530888c7c28c5c1556114db03a6cd7369fe6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649860"
---
# <a name="throw-activity-designer"></a>Throw, projektant działań

Projektant działań **throw** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.Throw>.

## <a name="the-throw-activity"></a>Działanie throw

Działanie <xref:System.Activities.Statements.Throw> zgłasza wyjątek.

### <a name="using-the-throw-activity-designer"></a>Korzystanie z projektanta działań throw

Dostęp do projektanta działań **throw** w kategorii **Obsługa błędów** w **przyborniku**.

Projektant działań **throw** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.Throw> z domyślną **nazwą wyświetlaną** throw. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **throw** lub w polu **DisplayName** siatki właściwości. Właściwość <xref:System.Activities.Statements.Throw.Exception%2A> musi być edytowana w siatce właściwości.

### <a name="the-throw-properties"></a>Właściwości throw

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Throw> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalną przyjazną nazwę działania <xref:System.Activities.Statements.Throw>. Wartość domyślna to throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Oznacza|Wyjątek do zgłoszenia. Ten wyjątek musi pochodzić od <xref:System.Exception>. Aby określić wyjątek, wpisz wyrażenie Visual Basic w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw, projektant działań](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)