---
title: 'Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b91e5f864bc15f1fbcab9400d0cd3a4a2e8224a9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299860"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Samouczek 2: Utworzenie kwizu matematycznego z limitem czasu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym samouczku utworzysz quiz, w którym powinieneś odpowiedzieć cztery losowe problemy arytmetyczne w określonym czasie. Omawiane kwestie:

- Generuj liczby losowe przy użyciu klasy `Random`.

- Wyzwalaj zdarzenia w określonym czasie przy użyciu kontrolki **czasomierza** .

- Sterowanie przepływem programu za pomocą instrukcji `if else`.

- Wykonaj podstawowe operacje arytmetyczne w kodzie.

  Po zakończeniu Quiz będzie wyglądał jak na poniższej ilustracji, z wyjątkiem innych liczb.

  ![Quiz matematyczny z czterema problemami](../ide/media/express-finishedquiz.png "Express_FinishedQuiz") Quiz utworzony w tym samouczku

> [!NOTE]
> Ten samouczek obejmuje wizualizacje C# i Visual Basic, dlatego należy skoncentrować się na informacjach specyficznych dla języka programowania, którego używasz.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1. Tworzenie projektu i dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Zacznij od utworzenia projektu, zmiany właściwości i dodania formantów `Label`.|
|[Krok 2. Tworzenie losowego problemu dodawania](../ide/step-2-create-a-random-addition-problem.md)|Utwórz problem z dodaniem i użyj klasy `Random`, aby wygenerować liczby losowe.|
|[Krok 3. Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md)|Dodaj czasomierz odliczania, aby można było przekroczyć limit czasu quizu.|
|[Krok 4. Dodawanie metody CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Dodaj metodę, aby sprawdzić, czy w ramach tego problemu została wprowadzona poprawna odpowiedź.|
|[Krok 5. Dodawanie procedur obsługi zdarzeń wprowadzania dla kontrolek NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Dodaj programy obsługi zdarzeń, które ułatwiają wykonywanie quizu.|
|[Krok 6. Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md)|Dodawanie problemu odejmowania, który generuje liczby losowe, używa czasomierza i sprawdza poprawność odpowiedzi.|
|[Krok 7. Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md)|Dodawanie problemów mnożenia i dzielenia, które generują liczby losowe, użyj czasomierza i sprawdzaj poprawność odpowiedzi.|
|[Krok 8. Dostosowywanie kwizu](../ide/step-8-customize-the-quiz.md)|Wypróbuj inne funkcje, takie jak zmiana kolorów i dodanie wskazówki.|
