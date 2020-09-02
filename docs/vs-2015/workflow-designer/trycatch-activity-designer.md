---
title: TryCatch — Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b26bb37d1ddeabb77b1399c6cbce5ae55b59702c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654661"
---
# <a name="trycatch-activity-designer"></a>TryCatch, projektant działań
Projektant działań **TryCatch** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.TryCatch> działania.

## <a name="the-trycatch-activity"></a>Działanie TryCatch
 <xref:System.Activities.Statements.TryCatch>Działanie zawiera <xref:System.Activities.Statements.TryCatch.Try%2A> działanie, kolekcję funkcji **Catch \<TException> ** i <xref:System.Activities.Statements.TryCatch.Finally%2A> Activity. A <xref:System.Activities.Statements.Catch%601> typu **TException** zawiera <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> a i <xref:System.Activities.Statements.Catch%601.Action%2A> . Są one używane do implementowania typowego mechanizmu obsługi błędów opartych na wyjątkach. <xref:System.Activities.Statements.TryCatch>Działanie próbuje wykonać <xref:System.Activities.Statements.TryCatch.Try%2A> działanie. Jeśli <xref:System.Activities.Statements.TryCatch.Try%2A> działanie zgłasza jakikolwiek wyjątek, <xref:System.Activities.Statements.TryCatch> działanie używa swojej kolekcji **TException \> do<przechwytywania** , aby dopasować wyjątek. Jeśli istnieje dopasowanie, to jest <xref:System.Activities.Statements.Catch%601.Action%2A> wykonywana odpowiednia wartość ** \<TException> catch** , która służy jako logika obsługi błędów dla wyjątku. Jeśli działania w <xref:System.Activities.Statements.TryCatch.Try%2A> sekcji zostały pomyślnie zakończone lub działania <xref:System.Activities.Statements.TryCatch.Catches%2A> wykonane pomyślnie, <xref:System.Activities.Statements.TryCatch> działanie wykonuje jego <xref:System.Activities.Statements.TryCatch.Finally%2A> działanie. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Wyjątki](https://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136).

### <a name="using-the-trycatch-activity-designer"></a>Korzystanie z projektanta działań TryCatch
 Projektanta działań **TryCatch** można znaleźć w kategorii **Obsługa błędów** w **przyborniku**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie okna [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub Ctlr + Alt + X).

 Projektanta działań **TryCatch** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.TryCatch> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> TryCatch. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań **TryCatch** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane na powierzchni projektanta działań **TryCatch** .

 Kliknij przycisk Rozwiń w prawym górnym rogu projektanta **TryCatch** , aby wyświetlić pola **try**, **catch**i **finally** w rozwiniętym widoku. Aby dodać catch, kliknij przycisk **Dodaj nowy catch** w programie **TryCatch** Designer. Przycisk zostanie zmieniony na pole kombi typu. Wybierz typ wyjątku i naciśnij klawisz ENTER, aby dodać catch. Po dodaniu **catch**zostanie rozwinięte miejsce przechwycenia, a działanie może zostać porzucone do przechwytywania w celu zdefiniowania logiki wykonywania dla catch. Zwróć uwagę, że po prawej stronie rozwiniętego obszaru catch znajduje się pole tekstowe. Można nazwać zmienną wyjątku przy użyciu tego pola tekstowego. Zmienna wyjątku może być używana tylko dla działań w ramach tego samego **przechwycenia**.

 Program **TryCatch** Designer nie obsługuje edytowania funkcji **przechwytywania**. Jeśli chcesz zmienić typ wyjątku, musisz usunąć **przechwycenie** i dodać nowy. **Catch** można usunąć, zaznaczając ją i usuwając lub używając menu **Usuń** w menu kontekstowym dostępnym po kliknięciu prawym przyciskiem myszy.

### <a name="the-trycatch-properties"></a>Właściwości TryCatch
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.TryCatch> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa opcjonalną przyjazną nazwę <xref:System.Activities.Statements.TryCatch> działania. Wartość domyślna to TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|Fałsz|Działanie wykonywane najpierw po wykonaniu <xref:System.Activities.Statements.TryCatch> .|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|Fałsz|Kolekcja elementów **przechwytywania** do sprawdzenia, gdy <xref:System.Activities.Statements.TryCatch.Try%2A> działanie zgłasza wyjątek.<br /><br /> W bloku należy dodać co najmniej jedno działanie <xref:System.Activities.Statements.TryCatch.Catches%2A> lub działanie <xref:System.Activities.Statements.TryCatch.Finally%2A> .|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|Fałsz|Działanie, które ma zostać wykonane, gdy <xref:System.Activities.Statements.TryCatch.Try%2A> i wszelkie niezbędne działania w <xref:System.Activities.Statements.TryCatch.Catches%2A> kolekcji zakończą wykonywanie.<br /><br /> W bloku należy dodać co najmniej jedno działanie <xref:System.Activities.Statements.TryCatch.Catches%2A> lub działanie <xref:System.Activities.Statements.TryCatch.Finally%2A> .|

## <a name="see-also"></a>Zobacz też
 [Collection](../workflow-designer/collection-activity-designers.md) [Rethrow](../workflow-designer/rethrow-activity-designer.md) [Zgłoszenie](../workflow-designer/throw-activity-designer.md) ponownego zgłoszenia kolekcji