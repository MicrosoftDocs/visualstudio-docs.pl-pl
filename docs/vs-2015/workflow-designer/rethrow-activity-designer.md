---
title: Ponownie zgłoś projektanta działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c65469242a60c64d6f31bfaea4fdbbf2d5251a34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663358"
---
# <a name="rethrow-activity-designer"></a>Rethrow, projektant działań
W celu utworzenia i skonfigurowania działania zostanie użyty Projektant działań **Rethrow** <xref:System.Activities.Statements.Rethrow> .

## <a name="the-rethrow-activity"></a>Działanie Rethrow
 <xref:System.Activities.Statements.Rethrow>Działanie zgłasza poprzednio zgłoszony wyjątek. To działanie może być używane tylko w <xref:System.Activities.Statements.Catch> obsłudze w <xref:System.Activities.Statements.TryCatch> działaniu.

### <a name="using-the-rethrow-activity-designer"></a>Korzystanie z programu Rethrow Designer
 Projektanta działań ponownego **wygenerowania** można znaleźć w kategorii **Obsługa błędów** w **przyborniku**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w lewej części okna [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Program **Rethrow** Designer może być przeciągany z **przybornika** i upuszczany na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.Rethrow> działania z domyślną wartością **DisplayName** elementu throw. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań **Rethrow** lub w polu **DisplayName** siatki właściwości.

### <a name="the-rethrow-properties"></a>Właściwości ponownego wygenerowania
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Rethrow> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa opcjonalną przyjazną nazwę <xref:System.Activities.Statements.Rethrow> działania. Wartość domyślna to Rethrow.|

## <a name="see-also"></a>Zobacz też
 [TryCatch](../workflow-designer/trycatch-activity-designer.md) [rzutowania](../workflow-designer/throw-activity-designer.md) [kolekcji](../workflow-designer/collection-activity-designers.md)