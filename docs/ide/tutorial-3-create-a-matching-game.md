---
title: 'samouczek 3: Tworzenie pasującej gry'
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 619c21f4878f2e421ee5ac5ea76a68cd6e6bc337
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579703"
---
# <a name="tutorial-3-create-a-matching-game"></a>samouczek 3: Tworzenie pasującej gry

W tym samouczku stworzysz grę w dopasowywanie, gdzie gracz musi dopasować pary ukrytych ikon.

> [!NOTE]
> W tym samouczku omówiono zarówno języka C#, jak i języka Visual Basic, więc skup się na informacjach specyficznych dla używanego języka programowania.

W tym samouczku przedstawiono następujące zadania:

- Przechowuj obiekty, takie jak ikony, w <xref:System.Collections.Generic.List%601> obiekcie.

- Użyj `foreach` pętli w języku `For Each` C# lub pętli w języku Visual Basic, aby iterować za pośrednictwem elementów na liście.

- Śledzić stan formularza za pomocą zmiennych odwołania.

- Stworzyć program obsługi zdarzeń w celu reagowania na zdarzenia, którego możesz używać z wieloma obiektami.

- Stworzyć czasomierz, który odlicza czas do zera, a następnie uruchamia zdarzenie dokładnie jeden raz po uruchomieniu.

Po zakończeniu aplikacja powinna wyglądać podobnie do następującego obrazu:

![Gra tworzona w ramach tego samouczka](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Łącza do samouczka

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1: Tworzenie projektu i dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Rozpocznij od utworzenia `TableLayoutPanel` projektu i dodania formantu, aby zapewnić prawidłowe wyrównanie formantów.|
|[Krok 2: Dodaj losowy obiekt i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Dodaj `Random` obiekt i `List` obiekt, aby utworzyć listę ikon.|
|[Krok 3: Przypisz losową ikonę do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md)|Przypisz ikony losowo `Label` do kontrolek, tak aby każda gra była inna.|
|[Krok 4: Dodaj program obsługi zdarzeń kliknięć do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Dodaj `Click` program obsługi zdarzeń, który zmienia kolor kliknowanego etykiety.|
|[Krok 5: Dodawanie odniesień do etykiet](../ide/step-5-add-label-references.md)|Dodaj zmienne odwołania, aby śledzić, które etykiety zostały kliknięte.|
|[Krok 6: Dodaj timer](../ide/step-6-add-a-timer.md)|Dodaj czasomierz do formularza, aby śledzić czas, który upłynął w grze.|
|[Krok 7: Utrzymuj widoczne pary](../ide/step-7-keep-pairs-visible.md)|Zachowaj widoczne pary ikon, jeśli wybrana para pasuje.|
|[Krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Dodaj `CheckForWinner()` metodę, aby sprawdzić, czy gracz wygrał.|
|[Krok 9: Wypróbuj inne funkcje](../ide/step-9-try-other-features.md)|Wypróbuj inne funkcje, takie jak zmiana ikon i kolorów, dodawanie siatki i dodawanie dźwięków. Spróbuj powiększyć planszę i dostosować czasomierz.|

Dostępne są również świetne, bezpłatne materiały do nauki wideo. Aby dowiedzieć się więcej o programowaniu w języku C#, zobacz [C# podstawy: Rozwój dla początkujących absolutnych](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej o programowaniu w języku Visual Basic, zobacz [Visual Basic podstawy: Rozwój dla początkujących .](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć samouczek, zacznij od **[kroku 1: Utwórz projekt i dodaj tabelę do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)**.

## <a name="see-also"></a>Zobacz też

* [Więcej samouczków języka C#](/visualstudio/get-started/csharp/)
* [Samouczki dotyczące języka Visual Basic](/visualstudio/get-started/visual-basic/)
* [Samouczki języka C++](/cpp/get-started/tutorial-console-cpp)
