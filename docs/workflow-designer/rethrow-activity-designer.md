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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114753"
---
# <a name="rethrow-activity-designer"></a>Rethrow, projektant działań

W celu utworzenia i skonfigurowania działania zostanie użyty Projektant działań **Rethrow** <xref:System.Activities.Statements.Rethrow> .

## <a name="the-rethrow-activity"></a>Działanie Rethrow

<xref:System.Activities.Statements.Rethrow>Działanie zgłasza poprzednio zgłoszony wyjątek. To działanie może być używane tylko w <xref:System.Activities.Statements.Catch> obsłudze w <xref:System.Activities.Statements.TryCatch> działaniu.

### <a name="use-the-rethrow-activity-designer"></a>Korzystanie z programu Rethrow Designer

Dostęp do programu **Rethrow** Designer w kategorii **Obsługa błędów** w **przyborniku**. Projektant działań **Rethrow** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Porzucenie projektanta działań powoduje utworzenie <xref:System.Activities.Statements.Rethrow> działania z domyślną **nazwą wyświetlaną** throw. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań ponownego **wygenerowania** lub w polu **DisplayName** siatki właściwości.

### <a name="the-rethrow-properties"></a>Właściwości ponownego wygenerowania

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Rethrow> właściwości i opisano, jak są one używane w projektancie:

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa opcjonalną przyjazną nazwę <xref:System.Activities.Statements.Rethrow> działania. Wartość domyślna to Rethrow.|

## <a name="see-also"></a>Zobacz też

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [Generować](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
