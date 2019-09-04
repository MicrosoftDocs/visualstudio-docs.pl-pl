---
title: 'Samouczek 2: Tworzenie quizu matematycznego z limitem czasu'
ms.date: 11/04/2016
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c0c7f3695be87f6cb4081b3aa02fc7a129869a4c
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293695"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Samouczek 2: Tworzenie quizu matematycznego z limitem czasu

W tym samouczku utworzysz quiz, w którym powinieneś odpowiedzieć cztery losowe problemy arytmetyczne w określonym czasie. Dowiesz się, jak:

- Generuj liczby losowe przy użyciu <xref:System.Random> klasy.

- Wyzwalaj zdarzenia w określonym czasie przy użyciu <xref:System.Windows.Forms.Timer> formantu.

- Sterowanie przepływem programu za `if else` pomocą instrukcji.

- Wykonaj podstawowe operacje arytmetyczne w kodzie.

Po zakończeniu Quiz będzie wyglądał jak na poniższej ilustracji, z wyjątkiem innych liczb:

![Quiz matematyczny z czterema problemami](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Linki samouczków

Aby pobrać kompletną wersję quizu, zobacz [kompletny przykładowy samouczek quizu Matematycznego](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

> [!NOTE]
> Ten samouczek obejmuje wizualizacje C# i Visual Basic, dlatego należy skoncentrować się na informacjach specyficznych dla języka programowania, którego używasz.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1. Tworzenie projektu i Dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Zacznij od utworzenia projektu, zmiany właściwości i dodania `Label` kontrolek.|
|[Krok 2. Utwórz losowy problem dodawania](../ide/step-2-create-a-random-addition-problem.md)|Utwórz problem z dodaniem i Użyj `Random` klasy w celu wygenerowania liczb losowych.|
|[Krok 3. Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md)|Dodaj czasomierz odliczania, aby można było przekroczyć limit czasu quizu.|
|[Krok 4. Dodaj metodę metody CheckTheAnswer ()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Dodaj metodę, aby sprawdzić, czy w ramach tego problemu została wprowadzona poprawna odpowiedź.|
|[Krok 5. Dodaj programy obsługi zdarzeń Enter dla kontrolek NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Dodaj programy obsługi zdarzeń, które ułatwiają wykonywanie quizu.|
|[Krok 6. Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md)|Dodawanie problemu odejmowania, który generuje liczby losowe, używa czasomierza i sprawdza poprawność odpowiedzi.|
|[Krok 7. Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md)|Dodawanie problemów mnożenia i dzielenia, które generują liczby losowe, użyj czasomierza i sprawdzaj poprawność odpowiedzi.|
|[Krok 8. Dostosowywanie quizu](../ide/step-8-customize-the-quiz.md)|Wypróbuj inne funkcje, takie jak zmiana kolorów i dodanie wskazówki.|
