---
title: 'Samouczek 2: Tworzenie quizu matematycznego z czasem'
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b1f3620ef462228ff6a3461f44019e9c515a1c0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579303"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Samouczek 2: Tworzenie quizu matematycznego z czasem

W tym samouczku tworzysz quiz, w którym osoba biorąca quiz musi odpowiedzieć na cztery losowe problemy arytmetyczne w określonym czasie.

> [!NOTE]
> W tym samouczku omówiono zarówno język C#, jak i język Visual Basic, więc skup się na informacjach specyficznych dla używanego języka programowania.

W tym samouczku przedstawiono następujące zadania:

- Generowanie liczb losowych <xref:System.Random> przy użyciu klasy.

- Zdarzenia wyzwalacza występują w określonym <xref:System.Windows.Forms.Timer> czasie przy użyciu formantu.

- Steruj przepływem programu przy użyciu `if else` instrukcji.

- Wykonywanie podstawowych operacji arytmetycznych w kodzie.

Po zakończeniu quiz będzie wyglądał podobnie do poniższego zrzutu ekranu, z wyjątkiem różnych liczb:

![Quiz matematyczny z czterema problemami](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Łącza do samouczka

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1: Tworzenie projektu i dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Zacznij od utworzenia projektu, zmiany właściwości `Label` i dodania formantów.|
|[Krok 2: Utwórz losowy problem z dodawaniem](../ide/step-2-create-a-random-addition-problem.md)|Utwórz problem z dodawaniem i użyj klasy do generowania `Random` liczb losowych.|
|[Krok 3: Dodaj minutnik](../ide/step-3-add-a-countdown-timer.md)|Dodaj minutnik, aby można było zdążać czas.|
|[Krok 4: Dodaj metodę CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Dodaj metodę, aby sprawdzić, czy osoba biorąca udział w quizie wprowadzona poprawna odpowiedź na ten problem.|
|[Krok 5: Dodaj programy obsługi zdarzeń Enter dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Dodaj programy obsługi zdarzeń, które ułatwiają korzystanie z quizu.|
|[Krok 6: Dodaj problem odejmowania](../ide/step-6-add-a-subtraction-problem.md)|Dodaj problem odejmowania, który generuje liczby losowe, używa czasomierza i sprawdza, czy nie ma poprawnych odpowiedzi.|
|[Krok 7: Dodaj problemy z mnożeniem i podziałem](../ide/step-7-add-multiplication-and-division-problems.md)|Dodaj problemy z mnożeniem i dzieleniem, które generują losowe liczby, użyj czasomierza i sprawdź, czy nie ma poprawnych odpowiedzi.|
|[Krok 8: Dostosuj quiz](../ide/step-8-customize-the-quiz.md)|Wypróbuj inne funkcje, takie jak zmiana kolorów i dodanie wskazówki.|

Dostępne są również świetne, bezpłatne materiały do nauki wideo. Aby dowiedzieć się więcej o programowaniu w języku C#, zobacz [C# podstawy: Rozwój dla początkujących absolutnych](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej o programowaniu w języku Visual Basic, zobacz [Visual Basic podstawy: Rozwój dla początkujących .](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć samouczek, zacznij od **[kroku 1: Utwórz projekt i dodaj etykiety do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)**.

## <a name="see-also"></a>Zobacz też

* [Więcej samouczków języka C#](/visualstudio/get-started/csharp/)
* [Samouczki dotyczące języka Visual Basic](/visualstudio/get-started/visual-basic/)
* [Samouczki języka C++](/cpp/get-started/tutorial-console-cpp)
