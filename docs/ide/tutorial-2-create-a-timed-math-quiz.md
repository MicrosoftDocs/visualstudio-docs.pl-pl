---
title: 'Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu'
description: Dowiedz się, jak utworzyć quiz, w którym musi odpowiedzieć cztery losowe problemy arytmetyczne w określonym czasie.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f86dbfd1d39b6a2c16b992fc6fe3a9313320d113
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971430"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu

W tym samouczku utworzysz quiz, w którym powinieneś odpowiedzieć cztery losowe problemy arytmetyczne w określonym czasie.

> [!NOTE]
> Ten samouczek obejmuje języki C# i Visual Basic, dlatego należy skoncentrować się na informacjach specyficznych dla języka programowania, którego używasz.

Ten samouczek przeprowadzi Cię przez następujące zadania:

- Generuj liczby losowe przy użyciu <xref:System.Random> klasy.

- Wyzwalaj zdarzenia w określonym czasie przy użyciu <xref:System.Windows.Forms.Timer> formantu.

- Sterowanie przepływem programu za pomocą `if else` instrukcji.

- Wykonaj podstawowe operacje arytmetyczne w kodzie.

Po zakończeniu Quiz będzie wyglądać podobnie do poniższego zrzutu ekranu, z wyjątkiem innych liczb:

![Quiz matematyczny z czterema problemami](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Linki samouczków

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1. Tworzenie projektu i dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Zacznij od utworzenia projektu, zmiany właściwości i dodania `Label` kontrolek.|
|[Krok 2. Tworzenie zadania z dodawaniem losowych liczb](../ide/step-2-create-a-random-addition-problem.md)|Utwórz problem z dodaniem i Użyj `Random` klasy w celu wygenerowania liczb losowych.|
|[Krok 3. Dodawanie czasomierza odliczającego w dół](../ide/step-3-add-a-countdown-timer.md)|Dodaj czasomierz odliczania, aby można było przekroczyć limit czasu quizu.|
|[Krok 4. Dodawanie metody CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Dodaj metodę, aby sprawdzić, czy w ramach tego problemu została wprowadzona poprawna odpowiedź.|
|[Krok 5. Dodawanie obsługi zdarzeń wprowadzania dla kontrolek NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Dodaj programy obsługi zdarzeń, które ułatwiają wykonywanie quizu.|
|[Krok 6. Dodawanie zadania z odejmowaniem](../ide/step-6-add-a-subtraction-problem.md)|Dodawanie problemu odejmowania, który generuje liczby losowe, używa czasomierza i sprawdza poprawność odpowiedzi.|
|[Krok 7. Dodawanie zadań z mnożeniem i dzieleniem](../ide/step-7-add-multiplication-and-division-problems.md)|Dodawanie problemów mnożenia i dzielenia, które generują liczby losowe, użyj czasomierza i sprawdzaj poprawność odpowiedzi.|
|[Krok 8. Dostosowywanie testu](../ide/step-8-customize-the-quiz.md)|Wypróbuj inne funkcje, takie jak zmiana kolorów i dodanie wskazówki.|

Dostępne są również wspaniałe, bezpłatne zasoby szkoleniowe dotyczące wideo. Aby dowiedzieć się więcej na temat programowania w języku C#, zobacz [podstawy języka c#: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w Visual Basic, zobacz [Visual Basic podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć pracę z samouczkiem, Zacznij od **[kroku 1: Tworzenie projektu i Dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)**.

## <a name="see-also"></a>Zobacz też

* [Więcej samouczków dotyczących języka C#](../get-started/csharp/index.yml)
* [Samouczki Visual Basic](../get-started/visual-basic/index.yml)
* [Samouczki języka C++](/cpp/get-started/tutorial-console-cpp)