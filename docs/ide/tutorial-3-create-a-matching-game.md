---
title: 'Samouczek 3: Utwórz pasujący obiekt typu gier'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a26f6b06c972d88ba1dfd56e8c3e4ebc1e4fed36
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943161"
---
# <a name="tutorial-3-create-a-matching-game"></a>Samouczek 3: Utwórz pasujący obiekt typu gier

W tym samouczku stworzysz grę w dopasowywanie, gdzie gracz musi dopasować pary ukrytych ikon. Dowiesz się, jak:

-   Store obiektów, takich jak ikony, w <xref:System.Collections.Generic.List%601> obiektu.

-   Użyj `foreach` pętli w języku Visual C# lub `For Each` pętli w języku Visual Basic do iteracji przez elementy na liście.

-   Śledzić stan formularza za pomocą zmiennych odwołania.

-   Stworzyć program obsługi zdarzeń w celu reagowania na zdarzenia, którego możesz używać z wieloma obiektami.

-   Stworzyć czasomierz, który odlicza czas do zera, a następnie uruchamia zdarzenie dokładnie jeden raz po uruchomieniu.

Po ukończeniu tego samouczka program będzie wyglądać jak na poniższym obrazie:

![Gra tworzona w ramach tego samouczka](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Samouczek łącza

Aby pobrać pełną wersję przykładu, zobacz [pełną pasującego przykładowy samouczek gry](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

> [!NOTE]
> W tym samouczku omówiono zarówno Visual C#, jak i Visual Basic, więc skoncentruj się na informacjach specyficznych dla języka programowania, którego używasz.

Jeśli masz problem lub pytania dotyczące programowania, spróbuj zadać pytanie na jednym z forów MSDN. Zobacz [forum języka Visual Basic](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) i [forum Visual C#](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral). Dostępne są tam również wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej na temat programowania w języku Visual Basic, zobacz [podstawy Visual Basic: Tworzenie dla całkowicie początkujących](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w języku Visual C#, zobacz [ C# podstawy: Tworzenie dla całkowicie początkujących](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1: Tworzenie projektu i Dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Rozpocznij od stworzenia projektu i dodawanie `TableLayoutPanel` formantu, aby zachować formanty prawidłowo wyrównane.|
|[Krok 2: Dodawanie obiektu losowego i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Dodaj `Random` obiektu i `List` obiekt, aby utworzyć listę ikon.|
|[Krok 3: Przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md)|Przypisz ikony losowo do `Label` kontroluje, tak aby każda gra była inna.|
|[Krok 4: Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Dodaj `Click` program obsługi zdarzeń, który zmienia kolor klikniętej etykiety.|
|[Krok 5: Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md)|Dodaj zmienne odwołania, aby śledzić, które etykiety zostały kliknięte.|
|[Krok 6: Dodaj czasomierz](../ide/step-6-add-a-timer.md)|Dodaj czasomierz do formularza, aby śledzić czas, który upłynął w grze.|
|[Krok 7: Zachować widoczność par](../ide/step-7-keep-pairs-visible.md)|Zachowaj widoczne pary ikon, jeśli wybrana para pasuje.|
|[Krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Dodaj `CheckForWinner()` metodę, aby sprawdzić, czy gracz wygrał.|
|[Krok 9: Spróbuj innych funkcji](../ide/step-9-try-other-features.md)|Wypróbuj inne funkcje, takie jak zmiana ikon i kolorów, dodawanie siatki i dodawanie dźwięków. Spróbuj powiększyć planszę i dostosować czasomierz.|
