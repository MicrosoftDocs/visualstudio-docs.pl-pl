---
title: 'Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu'
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 884047237652f6b69bd437b5faf47d820903b824
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588671"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu

W tym samouczku utworzysz quiz, w którym powinieneś odpowiedzieć cztery losowe problemy arytmetyczne w określonym czasie.

> [!NOTE]
> W tym samouczku C# omówiono zarówno program, jak i Visual Basic, dlatego należy skoncentrować się na informacjach specyficznych dla języka programowania, którego używasz.

Ten samouczek przeprowadzi Cię przez następujące zadania:

- Generuj liczby losowe przy użyciu klasy <xref:System.Random>.

- Wyzwalaj zdarzenia w określonym czasie przy użyciu kontrolki <xref:System.Windows.Forms.Timer>.

- Sterowanie przepływem programu za pomocą instrukcji `if else`.

- Wykonaj podstawowe operacje arytmetyczne w kodzie.

Po zakończeniu Quiz będzie wyglądać podobnie do poniższego zrzutu ekranu, z wyjątkiem innych liczb:

![Quiz matematyczny z czterema problemami](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Linki samouczków

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1. Tworzenie projektu i Dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Zacznij od utworzenia projektu, zmiany właściwości i dodania formantów `Label`.|
|[Krok 2. Tworzenie losowego problemu dodawania](../ide/step-2-create-a-random-addition-problem.md)|Utwórz problem z dodaniem i użyj klasy `Random`, aby wygenerować liczby losowe.|
|[Krok 3. Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md)|Dodaj czasomierz odliczania, aby można było przekroczyć limit czasu quizu.|
|[Krok 4. Dodawanie metody metody CheckTheAnswer ()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Dodaj metodę, aby sprawdzić, czy w ramach tego problemu została wprowadzona poprawna odpowiedź.|
|[Krok 5. Dodawanie obsługi zdarzeń Enter dla kontrolek NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Dodaj programy obsługi zdarzeń, które ułatwiają wykonywanie quizu.|
|[Krok 6. Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md)|Dodawanie problemu odejmowania, który generuje liczby losowe, używa czasomierza i sprawdza poprawność odpowiedzi.|
|[Krok 7. Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md)|Dodawanie problemów mnożenia i dzielenia, które generują liczby losowe, użyj czasomierza i sprawdzaj poprawność odpowiedzi.|
|[Krok 8. Dostosowywanie quizu](../ide/step-8-customize-the-quiz.md)|Wypróbuj inne funkcje, takie jak zmiana kolorów i dodanie wskazówki.|

Dostępne są również wspaniałe, bezpłatne zasoby szkoleniowe dotyczące wideo. Aby dowiedzieć się więcej na C#temat programowania w programie, zobacz [ C# podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w Visual Basic, zobacz [Visual Basic podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć pracę z samouczkiem, Zacznij od **[kroku 1: Tworzenie projektu i Dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)** .

## <a name="see-also"></a>Zobacz także

* [Więcej C# samouczków](/visualstudio/get-started/csharp/)
* [Samouczki Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++Podręcznik](/cpp/get-started/tutorial-console-cpp)
