---
title: Krok 2. Tworzenie zadania z dodawaniem losowych liczb
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5b83edaec6b81c3a2c5699184c62dbd70d71913
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416877"
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2. Tworzenie zadania z dodawaniem losowych liczb
W drugiej części tego samouczka nastąpi wyzwanie quizu poprzez dodanie problemów matematycznych, które są oparte na liczbie losowej. Należy również utworzyć metodę o nazwie `StartTheQuiz()` i wypełniającą problemy i uruchamiając odliczanie czasomierza. W dalszej części tego samouczka dodasz problemy odejmowania, mnożenia i dzielenia.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, [zobacz Samouczek 2: Utwórz Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md)matematyczny z limitem czasu.

## <a name="to-create-a-random-addition-problem"></a>Aby utworzyć losowy problem dodawania

1. W projektancie formularzy wybierz formularz (**Form1**).

2. Na pasku menu wybierz polecenie **Wyświetl** > **kod**.

     *Form1.cs* lub *Form1. vb* pojawia się w zależności od używanego języka programowania, aby można było wyświetlić kod związany z formularzem.

3. Utwórz obiekt przez `new` dodanie instrukcji w górnej części kodu, tak jak poniżej. <xref:System.Random>

     [!code-csharp[VbExpressTutorial3Step2#1](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_1.cs)]
     [!code-vb[VbExpressTutorial3Step2#1](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_1.vb)]

     Do formularza został dodany losowy obiekt i nazwany się **losowo**obiekt.

     `Random`jest znany jako obiekt. Prawdopodobnie wysłuchuje ten wyraz wcześniej i dowiesz się więcej na temat tego, co oznacza programowanie w następnym samouczku. Na razie Pamiętaj, że możesz użyć `new` instrukcji, aby tworzyć przyciski, etykiety, panele, OpenFileDialogs, ColorDialog, SoundPlayer, losowo i nawet formularze, a te elementy są określane jako obiekty. Po uruchomieniu programu formularz jest uruchamiany, a związany z nim kod tworzy losowy obiekt i nazywa je **losowo**.

     Wkrótce utworzysz metodę w celu sprawdzenia odpowiedzi, więc quiz musi używać zmiennych do przechowywania liczb losowych generowanych dla każdego problemu. Zobacz [zmienne](/dotnet/visual-basic/programming-guide/language-features/variables/index) lub [typy](/dotnet/csharp/programming-guide/types/index). Aby prawidłowo używać zmiennych, należy je zadeklarować, co oznacza, że lista ich nazw i typów danych.

4. Dodaj dwie zmienne całkowite do formularza i nadaj im nazwę **addend1** i **addend2**.

    > [!NOTE]
    > Zmienna typu Integer jest znana jako int in C# lub integer w Visual Basic. Ten rodzaj zmiennej przechowuje liczbę dodatnią lub ujemną od-2147483648 do 2147483647 i może przechowywać tylko liczby całkowite, nie dziesiętną.

     Używając podobnej składni, można dodać zmienną całkowitą w miarę dodawania losowego obiektu, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial3Step2#2](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_2.cs)]
     [!code-vb[VbExpressTutorial3Step2#2](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_2.vb)]

5. Dodaj metodę o nazwie `StartTheQuiz()` i, która używa <xref:System.Random.Next> metody losowego obiektu do wyświetlania liczb losowych w etykietach. `StartTheQuiz()`ostatecznie wprowadzi wszystkie problemy, a następnie uruchomi czasomierz, dodając komentarz. Funkcja powinna wyglądać następująco.

     [!code-csharp[VbExpressTutorial3Step2#3](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_3.cs)]
     [!code-vb[VbExpressTutorial3Step2#3](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_3.vb)]

     Zwróć uwagę, że po wprowadzeniu kropki (.) `randomizer` po wpisaniu w kodzie zostanie otwarte okno IntelliSense zawierające wszystkie metody losowego obiektu, które można wywołać. Na przykład technologia IntelliSense wyświetla listę `Next()` metody w następujący sposób.

     ![Następna Metoda](../ide/media/express_randomwhite.png) Następna Metoda

     Po wprowadzeniu kropki po obiekcie funkcja IntelliSense wyświetla listę elementów członkowskich obiektu, takich jak właściwości, metody i zdarzenia.

    > [!NOTE]
    > Gdy używasz `Next()` metody `Random` z obiektem, na przykład podczas wywoływania `randomizer.Next(50)`, otrzymasz liczbę losową o wartości mniejszej niż 50 (od 0 do 49). W tym przykładzie wywołano `randomizer.Next(51)`. Użyto 51, a nie 50, aby dwie liczby losowe dodali do odpowiedzi od 0 do 100. W przypadku przekazania 50 do `Next()` metody wybierana jest liczba od 0 do 49, więc największą możliwą odpowiedzią jest 98, nie 100. Po uruchomieniu pierwszych dwóch instrukcji w metodzie każda z dwóch zmiennych całkowitych, **addend1** i **addend2**, utrzymuje liczbę losową z zakresu od 0 do 50. Ten zrzut ekranu przedstawia C# kod wizualizacji, ale technologia IntelliSense działa tak samo jak w przypadku Visual Basic.

     Zapoznaj się bliżej z tymi instrukcjami.

     [!code-csharp[VbExpressTutorial3Step2#18](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_4.cs)]
     [!code-vb[VbExpressTutorial3Step2#18](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_4.vb)]

     Instrukcje ustawiają właściwości **tekstu** **plusLeftLabel** i **plusRightLabel** , tak aby wyświetlały dwie liczby losowe. Aby przekonwertować liczby na tekst, `ToString()` należy użyć metody całkowitej. (W programowaniu ciąg oznacza tekst. Kontrolki etykiet wyświetlają tylko tekst, nie liczby.

6. W oknie projektowania kliknij dwukrotnie przycisk **Start** lub wybierz go, a następnie wybierz klawisz **Enter** .

     Gdy użytkownik quizu wybierze ten przycisk, Quiz powinien zacząć pracę i po prostu dodał procedurę obsługi zdarzeń kliknięcia, aby zaimplementować to zachowanie.

7. Dodaj dwie poniższe instrukcje.

     [!code-csharp[VbExpressTutorial3Step2#4](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_5.cs)]
     [!code-vb[VbExpressTutorial3Step2#4](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_5.vb)]

     Pierwsza instrukcja wywołuje nową `StartTheQuiz()` metodę. Druga instrukcja ustawia właściwość **Enabled** formantu **startButton** na **wartość false** , aby nie można było wybrać przycisku w trakcie quizu.

8. Zapisz swój kod, uruchom go, a następnie wybierz przycisk **Start** .

     Pojawia się losowy błąd dodawania, jak pokazano na poniższej ilustracji.

     ![Problem losowego](../ide/media/express_additionproblem.png) dodawania losowego problemu podczas dodawania

     W następnym kroku samouczka dodasz sumę.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 3: Dodawanie czasomierza](../ide/step-3-add-a-countdown-timer.md)odliczania.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1: Tworzenie projektu i Dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
