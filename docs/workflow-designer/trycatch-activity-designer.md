---
title: Projektant przepływu pracy — Projektant działań TryCatch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76a7600cdab94499e13592924efabba2fb4c2faf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649807"
---
# <a name="trycatch-activity-designer"></a>TryCatch, projektant działań

Projektant działań **TryCatch** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.TryCatch>.

## <a name="the-trycatch-activity"></a>Działanie TryCatch
 Działanie <xref:System.Activities.Statements.TryCatch> zawiera działanie <xref:System.Activities.Statements.TryCatch.Try%2A>, kolekcję **\<TException Catch >** i działanie <xref:System.Activities.Statements.TryCatch.Finally%2A>. @No__t_0 typu **TException** zawiera <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> i <xref:System.Activities.Statements.Catch%601.Action%2A>. Są one używane do implementowania typowego mechanizmu obsługi błędów opartych na wyjątkach. Działanie <xref:System.Activities.Statements.TryCatch> próbuje wykonać <xref:System.Activities.Statements.TryCatch.Try%2A> działania. Jeśli działanie <xref:System.Activities.Statements.TryCatch.Try%2A> zgłosi jakikolwiek wyjątek, działanie <xref:System.Activities.Statements.TryCatch> używa swojej kolekcji **TException < przechwytywania \>** , aby dopasować wyjątek. Jeśli istnieje dopasowanie, <xref:System.Activities.Statements.Catch%601.Action%2A> odpowiedniej **> przechwytywania \<TException** zostanie wykonane, co służy jako logika obsługi błędów dla wyjątku. W przypadku pomyślnego ukończenia działań w sekcji <xref:System.Activities.Statements.TryCatch.Try%2A> lub działania w <xref:System.Activities.Statements.TryCatch.Catches%2A> pomyślnie wykonane działanie <xref:System.Activities.Statements.TryCatch> wykonuje jego działanie <xref:System.Activities.Statements.TryCatch.Finally%2A>. Aby uzyskać więcej informacji, zobacz [wyjątki przepływu pracy systemu Windows](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Korzystanie z projektanta działań TryCatch

Dostęp do projektanta działań **TryCatch** w kategorii **Obsługa błędów** w **przyborniku**.

Projektanta działań **TryCatch** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.TryCatch> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> TryCatch. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **TryCatch** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane na powierzchni projektanta działań **TryCatch** .

Kliknij przycisk Rozwiń w prawym górnym rogu projektanta **TryCatch** , aby wyświetlić pola **try**, **catch**i **finally** w rozwiniętym widoku. Aby dodać catch, kliknij przycisk **Dodaj nowy catch** w programie **TryCatch** Designer. Przycisk zostanie zmieniony na pole kombi typu. Wybierz typ wyjątku i naciśnij klawisz ENTER, aby dodać catch. Po dodaniu **catch**zostanie rozwinięte miejsce przechwycenia, a działanie może zostać porzucone do przechwytywania w celu zdefiniowania logiki wykonywania dla catch. Zwróć uwagę, że po prawej stronie rozwiniętego obszaru catch znajduje się pole tekstowe. Można nazwać zmienną wyjątku przy użyciu tego pola tekstowego. Zmienna wyjątku może być używana tylko dla działań w ramach tego samego **przechwycenia**.

Program **TryCatch** Designer nie obsługuje edytowania funkcji **przechwytywania**. Jeśli chcesz zmienić typ wyjątku, musisz usunąć **przechwycenie** i dodać nowy. **Catch** można usunąć, zaznaczając ją i usuwając lub wybierając pozycję **Usuń** w menu kontekstowym dostępnym przez kliknięcie prawym przyciskiem myszy.

### <a name="the-trycatch-properties"></a>Właściwości TryCatch

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.TryCatch>properties i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalną przyjazną nazwę działania <xref:System.Activities.Statements.TryCatch>. Wartość domyślna to TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Działanie wykonywane najpierw po wykonaniu <xref:System.Activities.Statements.TryCatch>.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Kolekcja elementów **przechwytywania** do sprawdzenia, gdy działanie <xref:System.Activities.Statements.TryCatch.Try%2A> zgłasza wyjątek.<br /><br /> Potrzebujesz co najmniej jednego działania w <xref:System.Activities.Statements.TryCatch.Catches%2A> lub działania w bloku <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Działanie, które ma zostać wykonane, gdy <xref:System.Activities.Statements.TryCatch.Try%2A> i wszelkie niezbędne działania w kolekcji <xref:System.Activities.Statements.TryCatch.Catches%2A> ukończą wykonywanie.<br /><br /> Potrzebujesz co najmniej jednego działania w <xref:System.Activities.Statements.TryCatch.Catches%2A> lub działania w bloku <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)