---
title: Krok 2. Tworzenie losowego problemu dodawania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54dee9c25fc9b8ddf1f8cf6c54c40d68ce53dc6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671861"
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2. Utworzenie problemu losowego dodawania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W drugiej części tego samouczka nastąpi wyzwanie quizu poprzez dodanie problemów matematycznych, które są oparte na liczbie losowej. Należy również utworzyć metodę o nazwie `StartTheQuiz()`, która wypełnia problemy i uruchamia odliczanie czasomierza. W dalszej części tego samouczka dodasz problemy odejmowania, mnożenia i dzielenia.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-create-a-random-addition-problem"></a>Aby utworzyć losowy problem dodawania

1. W projektancie formularzy wybierz formularz (Form1).

2. Na pasku menu wybierz **Widok**, **kod**.

     Form1.cs lub Form1. vb pojawia się w zależności od używanego języka programowania, aby można było wyświetlić kod związany z formularzem.

3. Utwórz obiekt `Random`, dodając instrukcję `new` w górnej części kodu, tak jak poniżej.

     [!code-csharp[VbExpressTutorial3Step2#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial3Step2#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#1)]

     Do formularza został dodany obiekt `Random` i jest on nazywany **losowym**obiektem.

     `Random` jest znany jako obiekt. Prawdopodobnie wysłuchuje ten wyraz wcześniej i dowiesz się więcej na temat tego, co oznacza programowanie w następnym samouczku. Na razie Pamiętaj, że możesz użyć instrukcji `new`, aby tworzyć przyciski, etykiety, panele, OpenFileDialogs, ColorDialog, SoundPlayer, losowo i nawet formularze, a te elementy są określane jako obiekty. Po uruchomieniu programu formularz jest uruchamiany, a związany z nim kod tworzy obiekt `Random` i nadaje mu nazwę **losowe**.

     Wkrótce utworzysz metodę w celu sprawdzenia odpowiedzi, więc quiz musi używać zmiennych do przechowywania liczb losowych generowanych dla każdego problemu. Zobacz [zmienne](https://msdn.microsoft.com/library/4cfaa06d-4ae3-4307-897b-cf599dc24caa) lub [typy](https://msdn.microsoft.com/library/f782d7cc-035e-4500-b1b1-36a9881130ad). Aby prawidłowo używać zmiennych, należy je zadeklarować, co oznacza, że lista ich nazw i typów danych.

4. Dodaj dwie zmienne całkowite do formularza i nadaj im nazwę **addend1** i **addend2**.

    > [!NOTE]
    > Zmienna typu Integer jest znana jako int in C# lub integer w Visual Basic. Ten rodzaj zmiennej przechowuje liczbę dodatnią lub ujemną od-2147483648 do 2147483647 i może przechowywać tylko liczby całkowite, nie dziesiętną.

     Używając podobnej składni, można dodać zmienną liczb całkowitych w miarę dodawania obiektu `Random`, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial3Step2#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial3Step2#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#2)]

5. Dodaj metodę o nazwie `StartTheQuiz()` i która używa metody `Next()` obiektu `Random` do wyświetlania liczb losowych w etykietach. `StartTheQuiz()` będzie ostatecznie wypełnić wszystkie problemy, a następnie uruchomić czasomierz, dodając komentarz. Funkcja powinna wyglądać następująco.

     [!code-csharp[VbExpressTutorial3Step2#3](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#3)]
     [!code-vb[VbExpressTutorial3Step2#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#3)]

     Należy zauważyć, że po wprowadzeniu kropki (.) po liczbie **losowej** w kodzie zostanie otwarte okno IntelliSense zawierające wszystkie metody obiektu `Random`, które można wywołać. Na przykład technologia IntelliSense wyświetla `Next()` metody w następujący sposób.

     ![Next — Metoda](../ide/media/express-randomwhite.png "Express_RandomWhite") Next — Metoda

     Po wprowadzeniu kropki po obiekcie funkcja IntelliSense wyświetla listę elementów członkowskich obiektu, takich jak właściwości, metody i zdarzenia.

    > [!NOTE]
    > Gdy używasz metody `Next()` z obiektem `Random`, na przykład podczas wywoływania `randomizer.Next(50)`, otrzymasz losową liczbę mniejszą niż 50 (od 0 do 49). W tym przykładzie wywołano `randomizer.Next(51)`. Użyto 51, a nie 50, aby dwie liczby losowe dodali do odpowiedzi od 0 do 100. Jeśli podano 50 do metody `Next()`, wybiera liczbę z przepustek od 0 do 49, więc największą możliwą odpowiedzią jest 98, nie 100. Po uruchomieniu dwóch pierwszych instrukcji w metodzie każda z dwóch zmiennych całkowitych, `addend1` i `addend2`, utrzymuje liczbę losową z zakresu od 0 do 50. Ten zrzut ekranu przedstawia C# kod wizualizacji, ale technologia IntelliSense działa tak samo jak w przypadku Visual Basic.

     Zapoznaj się bliżej z tymi instrukcjami.

     [!code-csharp[VbExpressTutorial3Step2#18](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#18)]
     [!code-vb[VbExpressTutorial3Step2#18](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#18)]

     Instrukcje ustawiają właściwości **tekstu** **plusLeftLabel** i **plusRightLabel** , tak aby wyświetlały dwie liczby losowe. Aby przekonwertować liczby na tekst, należy użyć metody `ToString()` Integer. (W programowaniu ciąg oznacza tekst. Kontrolki etykiet wyświetlają tylko tekst, nie liczby.

6. W oknie projektowania kliknij dwukrotnie przycisk **Start** lub wybierz go, a następnie wybierz klawisz ENTER.

     Gdy użytkownik quizu wybierze ten przycisk, Quiz powinien zacząć pracę i po prostu dodał procedurę obsługi zdarzeń kliknięcia, aby zaimplementować to zachowanie.

7. Dodaj dwie poniższe instrukcje.

     [!code-csharp[VbExpressTutorial3Step2#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial3Step2#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#4)]

     Pierwsza instrukcja wywołuje nową metodę `StartTheQuiz()`. Druga instrukcja ustawia właściwość **Enabled** formantu **startButton** na **wartość false** , aby nie można było wybrać przycisku w trakcie quizu.

8. Zapisz swój kod, uruchom go, a następnie wybierz przycisk **Start** .

     Pojawia się losowy błąd dodawania, jak pokazano na poniższej ilustracji.

     ![Problem losowego dodawania](../ide/media/express-additionproblem.png "Express_AdditionProblem") Problem losowego dodawania

     W następnym kroku samouczka dodasz sumę.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 3: Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1. Tworzenie projektu i Dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
