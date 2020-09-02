---
title: Komunikaty o błędach w Projektant przepływu pracy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d89c0dcad23a91ec6057311b9afde7d6d4702772
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656754"
---
# <a name="error-messages-in-workflow-designer"></a>Komunikaty o błędach w Projektancie przepływu pracy
W tym temacie opisano typy komunikatów o błędach, które można napotkać podczas pracy z programem [!INCLUDE[wfd1](../includes/wfd1-md.md)] .

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Sytuacje, w których wystąpią błędy w Projektant przepływu pracy
 Błędy [!INCLUDE[wfd2](../includes/wfd2-md.md)] występujące w następujących sytuacjach:

1. Wyrażenie zawiera błąd.

2. Ograniczenia walidacji działania nie zostały spełnione.

3. W pliku XAML występują błędy powodujące niepowodzenie załadowania działania.

4. W pliku XAML występują błędy, które powodują niepowodzenie ładowania przepływu pracy.

   Nieprawidłowe wyrażenia i niespełnione ograniczenia sprawdzania poprawności nie powodują skompilowania przepływu pracy. Kompilowanie przepływu pracy powiedzie się, ale <xref:System.Activities.InvalidWorkflowException> jest zgłaszane w czasie wykonywania. W przypadku wystąpienia błędów w pliku XAML kompilacja zakończy się niepowodzeniem.

   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]W przypadku załadowania przepływu pracy jego błędy są wyświetlane w **Lista błędów**. Aby przejść do działania, które jest źródłem błędu, kliknij dwukrotnie błąd w **Lista błędów**.

### <a name="expression-errors"></a>Błędy wyrażeń
 Nieprawidłowe wyrażenie jest oznaczane czerwonym kółkiem o białym znaku wykrzyknika obok wyrażenia. Umieszczenie wskaźnika myszy na tej ikonie spowoduje wyświetlenie etykietki narzędzia opisującej Źródło błędu. W obszarze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , kliknij wyrażenie, aby wyświetlić wiersz, który podkreśla Źródło błędu. Umieszczenie wskaźnika myszy nad tekstem w wierszu powoduje wyświetlenie etykietki narzędzia opisującej Źródło błędu.

### <a name="activity-validation-errors"></a>Błędy walidacji działania
 Gdy nie spełniono ograniczeń walidacji działania, w prawym górnym rogu działania pojawi się czerwony okrąg z białym znakiem. Umieszczenie wskaźnika myszy na tej ikonie spowoduje wyświetlenie etykietki narzędzia opisującej Źródło błędu.

### <a name="xaml-load-errors"></a>Błędy ładowania XAML
 Gdy działanie nie powiedzie się, nie można załadować czerwonego pola z tekstem "działanie nie mogło zostać załadowane z powodu błędów w kodzie XAML". Zwykle zdarza się to, gdy nie można rozpoznać typu działania. Nieprawidłowe działanie można usunąć w projektancie, zaznaczając czerwoną ramkę i usuwając ją.

### <a name="workflow-load-errors"></a>Błędy ładowania przepływu pracy
 W przypadku niepowodzenia ładowania przepływu pracy tekst "Projektant przepływu pracy napotkał problemy z dokumentem" pojawia się na powierzchni projektanta wraz z informacjami o wyjątku, które spowodowały niepowodzenie ładowania przepływu pracy. Zwykle zdarza się to, gdy nie można przeanalizować pliku XAML.