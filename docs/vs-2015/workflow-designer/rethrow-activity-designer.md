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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663358"
---
# <a name="rethrow-activity-designer"></a>Rethrow, projektant działań
W celu utworzenia i skonfigurowania działania <xref:System.Activities.Statements.Rethrow> jest używany Projektant działań **Rethrow** .

## <a name="the-rethrow-activity"></a>Działanie Rethrow
 Działanie <xref:System.Activities.Statements.Rethrow> zgłasza poprzednio zgłoszony wyjątek. To działanie może być używane tylko w obsłudze <xref:System.Activities.Statements.Catch> w działaniu <xref:System.Activities.Statements.TryCatch>.

### <a name="using-the-rethrow-activity-designer"></a>Korzystanie z programu Rethrow Designer
 Projektanta działań ponownego **wygenerowania** można znaleźć w kategorii **Obsługa błędów** w **przyborniku**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie, wybierając pozycję **pasek narzędzi** z  **Menu Widok** lub CTRL + ALT + X.)

 Projektant **działań ponownego** zgłoszenia można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.Rethrow> z domyślną **nazwą wyświetlaną** throw. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań ponownego **wygenerowania** lub w polu **DisplayName** siatki właściwości.

### <a name="the-rethrow-properties"></a>Właściwości ponownego wygenerowania
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Rethrow> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalną przyjazną nazwę działania <xref:System.Activities.Statements.Rethrow>. Wartość domyślna to Rethrow.|

## <a name="see-also"></a>Zobacz też
 [TryCatch](../workflow-designer/trycatch-activity-designer.md) [rzutowania](../workflow-designer/throw-activity-designer.md) [kolekcji](../workflow-designer/collection-activity-designers.md)