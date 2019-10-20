---
title: Komunikaty o błędach w Projektancie przepływu pracy
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1406802f85c755d4dab25e000843a995be252d0a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650498"
---
# <a name="error-messages-in-workflow-designer"></a>Komunikaty o błędach w Projektancie przepływu pracy

W tym temacie opisano typy komunikatów o błędach, które można napotkać podczas pracy z Projektant przepływu pracy.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Sytuacje, w których wystąpią błędy w Projektant przepływu pracy

Błędy w Projektant przepływu pracy odbywają się w następujących sytuacjach:

1. Wyrażenie zawiera błąd.

2. Ograniczenia walidacji działania nie zostały spełnione.

3. W pliku XAML występują błędy powodujące niepowodzenie załadowania działania.

4. W pliku XAML występują błędy, które powodują niepowodzenie ładowania przepływu pracy.

Nieprawidłowe wyrażenia i niespełnione ograniczenia sprawdzania poprawności nie powodują skompilowania przepływu pracy. Kompilowanie przepływu pracy powiedzie się, ale w czasie wykonywania zostanie zgłoszone <xref:System.Activities.InvalidWorkflowException>. W przypadku wystąpienia błędów w pliku XAML kompilacja zakończy się niepowodzeniem.

W programie Visual Studio, gdy przepływ pracy jest ładowany, jego błędy są wyświetlane w **Lista błędów**. Aby przejść do działania, które jest źródłem błędu, kliknij dwukrotnie błąd w **Lista błędów**.

### <a name="expression-errors"></a>Błędy wyrażeń
 Nieprawidłowe wyrażenie jest oznaczane czerwonym kółkiem o białym znaku wykrzyknika obok wyrażenia. Umieszczenie wskaźnika myszy na tej ikonie spowoduje wyświetlenie etykietki narzędzia opisującej Źródło błędu. W programie Visual Studio kliknij wyrażenie, aby wyświetlić wiersz, który podkreśla Źródło błędu. Umieszczenie wskaźnika myszy nad tekstem w wierszu powoduje wyświetlenie etykietki narzędzia opisującej Źródło błędu.

### <a name="activity-validation-errors"></a>Błędy walidacji działania
 Gdy nie spełniono ograniczeń walidacji działania, w prawym górnym rogu działania pojawi się czerwony okrąg z białym znakiem. Umieszczenie wskaźnika myszy na tej ikonie spowoduje wyświetlenie etykietki narzędzia opisującej Źródło błędu.

### <a name="xaml-load-errors"></a>Błędy ładowania XAML
 Gdy działanie nie powiedzie się, nie można załadować czerwonego pola z tekstem "działanie nie mogło zostać załadowane z powodu błędów w kodzie XAML". Zwykle zdarza się to, gdy nie można rozpoznać typu działania. Nieprawidłowe działanie można usunąć w projektancie, zaznaczając czerwoną ramkę i usuwając ją.

### <a name="workflow-load-errors"></a>Błędy ładowania przepływu pracy
 W przypadku niepowodzenia ładowania przepływu pracy tekst "Projektant przepływu pracy napotkał problemy z dokumentem" pojawia się na powierzchni projektanta wraz z informacjami o wyjątku, które spowodowały niepowodzenie ładowania przepływu pracy. Zwykle zdarza się to, gdy nie można przeanalizować pliku XAML.