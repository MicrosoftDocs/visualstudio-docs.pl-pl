---
title: 'Samouczek 3: Tworzenie gry w dopasowywanie'
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5161f81aaf3edf654a5979f6226449bc52604167
ms.sourcegitcommit: 6244689e742e551e7b6933959bd42df56928ece3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72516583"
---
# <a name="tutorial-3-create-a-matching-game"></a>Samouczek 3: Tworzenie gry w dopasowywanie

W tym samouczku stworzysz grę w dopasowywanie, gdzie gracz musi dopasować pary ukrytych ikon.

> [!NOTE]
> W tym samouczku C# omówiono zarówno program, jak i Visual Basic, dlatego należy skoncentrować się na informacjach specyficznych dla języka programowania, którego używasz.

Ten samouczek przeprowadzi Cię przez następujące zadania:

- Przechowywanie obiektów, takich jak ikony, w obiekcie <xref:System.Collections.Generic.List%601>.

- Użyj pętli `foreach` w C# pętli `For Each` w Visual Basic, aby wykonać iterację elementów na liście.

- Śledzić stan formularza za pomocą zmiennych odwołania.

- Stworzyć program obsługi zdarzeń w celu reagowania na zdarzenia, którego możesz używać z wieloma obiektami.

- Stworzyć czasomierz, który odlicza czas do zera, a następnie uruchamia zdarzenie dokładnie jeden raz po uruchomieniu.

Po zakończeniu aplikacja powinna wyglądać podobnie do poniższej ilustracji:

![Gra tworzona w ramach tego samouczka](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Linki samouczków

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1. Tworzenie projektu i Dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Zacznij od utworzenia projektu i dodania kontrolki `TableLayoutPanel`, aby zachować poprawne wyrównywanie kontrolek.|
|[Krok 2. Dodawanie losowego obiektu i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Dodaj obiekt `Random` i obiekt `List`, aby utworzyć listę ikon.|
|[Krok 3. przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md)|Przypisz ikony losowo do kontrolek `Label`, tak aby każda gra była inna.|
|[Krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Dodaj procedurę obsługi zdarzeń `Click`, która zmienia kolor klikniętej etykiety.|
|[Krok 5. Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md)|Dodaj zmienne odwołania, aby śledzić, które etykiety zostały kliknięte.|
|[Krok 6. Dodawanie czasomierza](../ide/step-6-add-a-timer.md)|Dodaj czasomierz do formularza, aby śledzić czas, który upłynął w grze.|
|[Krok 7. zachowanie widoczności par](../ide/step-7-keep-pairs-visible.md)|Zachowaj widoczne pary ikon, jeśli wybrana para pasuje.|
|[Krok 8. Dodanie metody w celu sprawdzenia, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Dodaj metodę `CheckForWinner()`, aby sprawdzić, czy odtwarzacz został wygrany.|
|[Krok 9. Wypróbuj inne funkcje](../ide/step-9-try-other-features.md)|Wypróbuj inne funkcje, takie jak zmiana ikon i kolorów, dodawanie siatki i dodawanie dźwięków. Spróbuj powiększyć planszę i dostosować czasomierz.|

Dostępne są również wspaniałe, bezpłatne zasoby szkoleniowe dotyczące wideo. Aby dowiedzieć się więcej na C#temat programowania w programie, zobacz [ C# podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w Visual Basic, zobacz [Visual Basic podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć pracę z samouczkiem, Zacznij od **[kroku 1: Tworzenie projektu i Dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)** .

## <a name="see-also"></a>Zobacz także

* [Więcej C# samouczków](/visualstudio/get-started/csharp/)
* [Samouczki Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++Podręcznik](/cpp/get-started/tutorial-console-cpp)
