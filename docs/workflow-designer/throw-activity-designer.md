---
title: Projektant przepływu pracy-throw — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 650082ab0e4f8576b7028b8011c88bf5d93b2afd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593099"
---
# <a name="throw-activity-designer"></a>Throw, projektant działań

Projektant działań **throw** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Throw> działania.

## <a name="the-throw-activity"></a>Działanie throw

<xref:System.Activities.Statements.Throw>Działanie zgłasza wyjątek.

### <a name="using-the-throw-activity-designer"></a>Korzystanie z projektanta działań throw

Dostęp do projektanta działań **throw** w kategorii **Obsługa błędów** w **przyborniku**.

Można przeciągać **projektanta działań z** **przybornika** i znajdować się na Projektant przepływu pracy powierzchni, wszędzie tam gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.Throw> działania z domyślną wartością **DisplayName** elementu throw. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań **throw** lub w polu **DisplayName** siatki właściwości. <xref:System.Activities.Statements.Throw.Exception%2A>Właściwość musi być edytowana w siatce właściwości.

### <a name="the-throw-properties"></a>Właściwości throw

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Throw> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa opcjonalną przyjazną nazwę <xref:System.Activities.Statements.Throw> działania. Wartość domyślna to throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Prawda|Wyjątek do zgłoszenia. Ten wyjątek musi pochodzić od <xref:System.Exception> . Aby określić wyjątek, wpisz wyrażenie Visual Basic w siatce właściwości.|

## <a name="see-also"></a>Zobacz też

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw, projektant działań](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
