---
title: 'Samouczek 3: Tworzenie gry w dopasowywanie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 30ee029fe231202c821c8448d3594192b5ebfdf8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299854"
---
# <a name="tutorial-3-create-a-matching-game"></a>Samouczek 3: Tworzenie gry w dopasowywanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym samouczku stworzysz grę w dopasowywanie, gdzie gracz musi dopasować pary ukrytych ikon. Omawiane kwestie:

- Przechowywanie obiektów, takich jak ikony, w obiekcie `List`.

- Użyj pętli `foreach` w wizualizacji C# lub pętli `For Each` w Visual Basic, aby wykonać iterację elementów na liście.

- Śledzić stan formularza za pomocą zmiennych odwołania.

- Stworzyć program obsługi zdarzeń w celu reagowania na zdarzenia, którego możesz używać z wieloma obiektami.

- Stworzyć czasomierz, który odlicza czas do zera, a następnie uruchamia zdarzenie dokładnie jeden raz po uruchomieniu.

  Po zakończeniu samouczka program będzie wyglądać tak, jak na poniższej ilustracji.

  ![Gra utworzona w tym samouczku](../ide/media/express-finishedgame.png "Express_FinishedGame") Gra utworzona w tym samouczku

> [!NOTE]
> W tym samouczku omówiono zarówno Visual C#, jak i Visual Basic, więc skoncentruj się na informacjach specyficznych dla języka programowania, którego używasz.

 Jeśli masz problem lub pytania dotyczące programowania, spróbuj zadać pytanie na jednym z forów MSDN. Zobacz [forum Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) i [forum C# wizualne](https://social.msdn.microsoft.com/Forums/en-US/home). Dostępne są tam również wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej na temat programowania w Visual Basic, zobacz [Visual Basic podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat C#programowania w wizualizacji, zobacz [ C# podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1. Tworzenie projektu i dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Zacznij od utworzenia projektu i dodania kontrolki `TableLayoutPanel`, aby zachować poprawne wyrównywanie kontrolek.|
|[Krok 2. Dodawanie obiektu Random i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Dodaj obiekt `Random` i obiekt `List`, aby utworzyć listę ikon.|
|[Krok 3. Przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md)|Przypisz ikony losowo do kontrolek `Label`, tak aby każda gra była inna.|
|[Krok 4. Dodawanie procedury obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Dodaj program obsługę zdarzeń Kliknij, który zmienia kolor klikniętej etykiety.|
|[Krok 5. Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md)|Dodaj zmienne odwołania, aby śledzić, które etykiety zostały kliknięte.|
|[Krok 6. Dodawanie czasomierza](../ide/step-6-add-a-timer.md)|Dodaj czasomierz do formularza, aby śledzić czas, który upłynął w grze.|
|[Krok 7. Zachowanie widoczności par](../ide/step-7-keep-pairs-visible.md)|Zachowaj widoczne pary ikon, jeśli wybrana para pasuje.|
|[Krok 8. Dodanie metody sprawdzania, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Dodaj metodę `CheckForWinner()`, aby sprawdzić, czy odtwarzacz został wygrany.|
|[Krok 9. Wypróbowanie innych funkcji](../ide/step-9-try-other-features.md)|Wypróbuj inne funkcje, takie jak zmiana ikon i kolorów, dodawanie siatki i dodawanie dźwięków. Spróbuj powiększyć planszę i dostosować czasomierz.|
