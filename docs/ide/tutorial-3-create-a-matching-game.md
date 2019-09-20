---
title: 'Samouczek 3: Tworzenie gry zgodnej'
ms.date: 11/04/2016
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8fafd46561b6a3628989b675b14c493b60da6fe
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118711"
---
# <a name="tutorial-3-create-a-matching-game"></a>Samouczek 3: Tworzenie gry zgodnej

W tym samouczku stworzysz grę w dopasowywanie, gdzie gracz musi dopasować pary ukrytych ikon. Dowiesz się, jak:

- Przechowywanie obiektów, takich jak ikony, w <xref:System.Collections.Generic.List%601> obiekcie.

- Użyj pętli w wizualizacji C# lub `For Each` pętli w Visual Basic, aby wykonać iterację elementów na liście. `foreach`

- Śledzić stan formularza za pomocą zmiennych odwołania.

- Stworzyć program obsługi zdarzeń w celu reagowania na zdarzenia, którego możesz używać z wieloma obiektami.

- Stworzyć czasomierz, który odlicza czas do zera, a następnie uruchamia zdarzenie dokładnie jeden raz po uruchomieniu.

Po zakończeniu pracy z tym samouczkiem program będzie wyglądać tak, jak na poniższej ilustracji:

![Gra tworzona w ramach tego samouczka](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Linki samouczków

Aby pobrać kompletną wersję przykładu, zobacz [kompletny przykładowy samouczek gry](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

> [!NOTE]
> W tym samouczku omówiono zarówno Visual C#, jak i Visual Basic, więc skoncentruj się na informacjach specyficznych dla języka programowania, którego używasz.

Jeśli masz problem lub pytania dotyczące programowania, spróbuj zadać pytanie na jednym z forów MSDN. Zobacz [forum Visual Basic](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) i [forum C# wizualne](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral). Dostępne są tam również wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej na temat programowania w [Visual Basic, zobacz Visual Basic podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat C#programowania w [ wizualizacji, zobacz C# podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1. Tworzenie projektu i Dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Zacznij od utworzenia projektu i dodania `TableLayoutPanel` kontrolki, aby zachować prawidłowe wyrównanie kontrolek.|
|[Krok 2. Dodaj losowy obiekt i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|`Random` Dodaj obiekt`List` i obiekt, aby utworzyć listę ikon.|
|[Krok 3. Przypisywanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md)|Przypisz ikony losowo do `Label` kontrolek, aby każda z nich była inna.|
|[Krok 4. Dodaj program obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Dodaj program obsługi zdarzeń, który zmienia kolor klikniętej etykiety. `Click`|
|[Krok 5. Dodaj odwołania do etykiet](../ide/step-5-add-label-references.md)|Dodaj zmienne odwołania, aby śledzić, które etykiety zostały kliknięte.|
|[Krok 6. Dodawanie czasomierza](../ide/step-6-add-a-timer.md)|Dodaj czasomierz do formularza, aby śledzić czas, który upłynął w grze.|
|[Krok 7. Zachowaj widoczne pary](../ide/step-7-keep-pairs-visible.md)|Zachowaj widoczne pary ikon, jeśli wybrana para pasuje.|
|[Krok 8. Dodaj metodę, aby sprawdzić, czy odtwarzacz został wygrany](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|`CheckForWinner()` Dodaj metodę, aby sprawdzić, czy odtwarzacz został wygrany.|
|[Krok 9. Wypróbuj inne funkcje](../ide/step-9-try-other-features.md)|Wypróbuj inne funkcje, takie jak zmiana ikon i kolorów, dodawanie siatki i dodawanie dźwięków. Spróbuj powiększyć planszę i dostosować czasomierz.|
