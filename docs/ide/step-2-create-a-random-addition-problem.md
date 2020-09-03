---
title: Krok 2. Tworzenie zadania z dodawaniem losowych liczb
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2febef6987cf3440f92f6a6c505840cfe3ca3448
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77579890"
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2. Tworzenie zadania z dodawaniem losowych liczb

W drugiej części tego samouczka nastąpi wyzwanie quizu poprzez dodanie problemów matematycznych, które są oparte na liczbie losowej. Należy również utworzyć metodę o nazwie `StartTheQuiz()` i wypełniającą problemy i uruchamiając odliczanie czasomierza. W dalszej części tego samouczka dodasz problemy odejmowania, mnożenia i dzielenia.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-random-addition-problem"></a>Aby utworzyć losowy problem dodawania

1. W projektancie formularzy wybierz formularz (**Form1**).

2. Na pasku menu wybierz polecenie **Wyświetl**  >  **kod**.

     *Form1.cs* lub *Form1. vb* pojawia się w zależności od używanego języka programowania, aby można było wyświetlić kod związany z formularzem.

3. Utwórz <xref:System.Random> obiekt przez dodanie instrukcji w `new` górnej części kodu, tak jak poniżej.

     [!code-csharp[VbExpressTutorial3Step2#1](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_1.cs)]
     [!code-vb[VbExpressTutorial3Step2#1](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_1.vb)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Do formularza został dodany losowy obiekt i nazwany się **losowo**obiekt.

     `Random` jest znany jako obiekt. Prawdopodobnie wysłuchuje ten wyraz wcześniej i dowiesz się więcej na temat tego, co oznacza programowanie w następnym samouczku. Na razie Pamiętaj, że możesz użyć instrukcji, `new` Aby tworzyć przyciski, etykiety, panele, OpenFileDialogs, ColorDialog, SoundPlayer, losowo i nawet formularze, a te elementy są określane jako obiekty. Po uruchomieniu programu formularz jest uruchamiany, a związany z nim kod tworzy losowy obiekt i nazywa je **losowo**.

     Wkrótce utworzysz metodę w celu sprawdzenia odpowiedzi, więc quiz musi używać zmiennych do przechowywania liczb losowych generowanych dla każdego problemu. Zobacz [zmienne](/dotnet/visual-basic/programming-guide/language-features/variables/index) lub [typy](/dotnet/csharp/programming-guide/types/index). Aby prawidłowo używać zmiennych, należy je zadeklarować, co oznacza, że lista ich nazw i typów danych.

4. Dodaj dwie zmienne całkowite do formularza i nadaj im nazwę **addend1** i **addend2**.

    > [!NOTE]
    > Zmienna typu Integer jest znana jako int w C# lub Integer w Visual Basic. Ten rodzaj zmiennej przechowuje liczbę dodatnią lub ujemną od-2147483648 do 2147483647 i może przechowywać tylko liczby całkowite, nie dziesiętną.

     Używając podobnej składni, można dodać zmienną całkowitą w miarę dodawania losowego obiektu, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial3Step2#2](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_2.cs)]
     [!code-vb[VbExpressTutorial3Step2#2](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_2.vb)]

5. Dodaj metodę o nazwie `StartTheQuiz()` i, która używa metody losowego obiektu <xref:System.Random.Next> do wyświetlania liczb losowych w etykietach. `StartTheQuiz()` ostatecznie wprowadzi wszystkie problemy, a następnie uruchomi czasomierz, dodając komentarz. Funkcja powinna wyglądać następująco.

     [!code-csharp[VbExpressTutorial3Step2#3](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_3.cs)]
     [!code-vb[VbExpressTutorial3Step2#3](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_3.vb)]

     Zwróć uwagę, że po wprowadzeniu kropki (.) po wpisaniu `randomizer` w kodzie zostanie otwarte okno IntelliSense zawierające wszystkie metody losowego obiektu, które można wywołać. Na przykład technologia IntelliSense wyświetla listę `Next()` metody w następujący sposób.

     ![Next — Metoda](../ide/media/express_randomwhite.png)<br/>
*Next — Metoda*

     Po wprowadzeniu kropki po obiekcie funkcja IntelliSense wyświetla listę elementów członkowskich obiektu, takich jak właściwości, metody i zdarzenia.

    > [!NOTE]
    > Gdy używasz `Next()` metody z `Random` obiektem, na przykład podczas wywoływania `randomizer.Next(50)` , otrzymasz liczbę losową o wartości mniejszej niż 50 (od 0 do 49). W tym przykładzie wywołano `randomizer.Next(51)` . Użyto 51, a nie 50, aby dwie liczby losowe dodali do odpowiedzi od 0 do 100. W przypadku przekazania 50 do `Next()` metody wybierana jest liczba od 0 do 49, więc największą możliwą odpowiedzią jest 98, nie 100. Po uruchomieniu pierwszych dwóch instrukcji w metodzie każda z dwóch zmiennych całkowitych, **addend1** i **addend2**, utrzymuje liczbę losową z zakresu od 0 do 50. Ten zrzut ekranu przedstawia kod C#, ale technologia IntelliSense działa tak samo jak w przypadku Visual Basic.

     Zapoznaj się bliżej z tymi instrukcjami.

     [!code-csharp[VbExpressTutorial3Step2#18](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_4.cs)]
     [!code-vb[VbExpressTutorial3Step2#18](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_4.vb)]

     Instrukcje ustawiają właściwości **tekstu** **plusLeftLabel** i **plusRightLabel** , tak aby wyświetlały dwie liczby losowe. `ToString()`Aby przekonwertować liczby na tekst, należy użyć metody całkowitej. (W programowaniu ciąg oznacza tekst. Kontrolki etykiet wyświetlają tylko tekst, nie liczby.

6. W oknie projektowania kliknij dwukrotnie przycisk **Start** lub wybierz go, a następnie wybierz klawisz **Enter** .

     Gdy użytkownik quizu wybierze ten przycisk, Quiz powinien zacząć pracę i po prostu dodał procedurę obsługi zdarzeń kliknięcia, aby zaimplementować to zachowanie.

7. Dodaj dwie poniższe instrukcje.

     [!code-csharp[VbExpressTutorial3Step2#4](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_5.cs)]
     [!code-vb[VbExpressTutorial3Step2#4](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_5.vb)]

     Pierwsza instrukcja wywołuje nową `StartTheQuiz()` metodę. Druga instrukcja ustawia właściwość **Enabled** formantu **startButton** na **wartość false** , aby nie można było wybrać przycisku w trakcie quizu.

8. Zapisz swój kod, uruchom go, a następnie wybierz przycisk **Start** .

     Pojawia się losowy błąd dodawania, jak pokazano na poniższym zrzucie ekranu.

     ![Problem losowego dodawania](../ide/media/express_additionproblem.png)<br/>
*Problem losowego dodawania*

     W następnym kroku samouczka dodasz sumę.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 3: Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1. Tworzenie projektu i Dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
