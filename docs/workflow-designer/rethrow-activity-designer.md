---
title: Projektant przepływu pracy — ponowne zgłoszenie projektanta działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cb73a674e702d54f970c5dea7ec051f100382c9
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114753"
---
# <a name="rethrow-activity-designer"></a>Rethrow, projektant działań

W celu utworzenia i skonfigurowania działania <xref:System.Activities.Statements.Rethrow> jest używany Projektant działań **Rethrow** .

## <a name="the-rethrow-activity"></a>Działanie Rethrow

Działanie <xref:System.Activities.Statements.Rethrow> zgłasza poprzednio zgłoszony wyjątek. To działanie może być używane tylko w obsłudze <xref:System.Activities.Statements.Catch> w działaniu <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Korzystanie z programu Rethrow Designer

Dostęp do programu **Rethrow** Designer w kategorii **Obsługa błędów** w **przyborniku**. Projektant **działań ponownego** zgłoszenia można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Porzucenie projektanta działań powoduje utworzenie działania <xref:System.Activities.Statements.Rethrow> z domyślną **nazwą wyświetlaną** throw. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań ponownego **wygenerowania** lub w polu **DisplayName** siatki właściwości.

### <a name="the-rethrow-properties"></a>Właściwości ponownego wygenerowania

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Rethrow> i opisano, jak są one używane w projektancie:

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa opcjonalną przyjazną nazwę działania <xref:System.Activities.Statements.Rethrow>. Wartość domyślna to Rethrow.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
