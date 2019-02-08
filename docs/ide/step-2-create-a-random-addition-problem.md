---
title: Krok 2. Utwórz problem losowego dodawania
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2897a94dca8210f5ebf11ab43b884108cc7171dd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931120"
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2. Utwórz problem losowego dodawania
W drugiej części tego samouczka należy quiz trudne, dodając zagadnienia matematyczne oparte na liczbach losowych. Możesz również utworzyć metodę, która nosi nazwę `StartTheQuiz()` i który wypełnia ona problemy i uruchamia minutnik. W dalszej części tego samouczka dodasz odejmowania, mnożenia i dzielenia problemów.

> [!NOTE]
>  Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby uzyskać omówienie samouczka, zobacz [samouczek 2: Utwórz quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-random-addition-problem"></a>Aby utworzyć losowy problem dodawania

1.  W Projektancie formularza wybierz formularz (**Form1**).

2.  Na pasku menu wybierz **widoku** > **kodu**.

     *Form1.cs* lub *Form1.vb* pojawia się, w zależności od języka programowania, którego używasz, dzięki czemu można wyświetlić kod związany z formularzem.

3.  Tworzenie <xref:System.Random> obiekt poprzez dodanie `new` instrukcji w górnej części kodu, podobnie do poniższego.

     [!code-csharp[VbExpressTutorial3Step2#1](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_1.cs)]
     [!code-vb[VbExpressTutorial3Step2#1](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_1.vb)]

     Zostały dodane do obiektu Random do formularza i nadano **randomizer**.

     `Random` jest znany jako obiekt. Prawdopodobnie słyszałeś już słowo, i Dowiedz się więcej na temat co to oznacza dla programowania w następnym samouczku. Teraz wystarczy pamiętać, że można użyć `new` instrukcji, aby utworzyć przyciski, etykiety, panele, okna Openfiledialog, Colordialog, SoundPlayer, Random i nawet formularze i te elementy są określane jako obiekty. Gdy uruchamiasz program, formularz zostaje uruchomiony, a kod związany z nim tworzy obiekt losowych i nadaje mu **randomizer**.

     Wkrótce będziesz tworzyć metodę sprawdzania odpowiedzi, dlatego quiz musi używać zmiennych do przechowywania liczb losowych, który generuje dla każdego problemu. Zobacz [zmienne](/dotnet/visual-basic/programming-guide/language-features/variables/index) lub [typy](/dotnet/csharp/programming-guide/types/index). Aby prawidłowo używać zmiennych, musisz je zadeklarować, co oznacza utworzenie listy ich nazwy i typy danych.

4.  Dodaj dwie zmienne liczby całkowitej do formularza i nazwij je **addend1** i **addend2**.

    > [!NOTE]
    >  Zmienną całkowitą jest znana jako int w języku C# lub liczba całkowita w języku Visual Basic. Tego typu zmienna przechowuje liczbę dodatnią lub ujemną od -2147483648 do 2147483647 i może przechowywać jedynie liczby całkowite, nie miejsca po przecinku.

     Podobnej składni umożliwia dodawanie zmienna typu Liczba całkowita, jak dodać obiekt losowy, co ilustruje poniższy kod.

     [!code-csharp[VbExpressTutorial3Step2#2](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_2.cs)]
     [!code-vb[VbExpressTutorial3Step2#2](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_2.vb)]

5.  Dodaj metodę o nazwie `StartTheQuiz()` i który korzysta z obiektu Random <xref:System.Random.Next> metodę do pokazania liczb losowych w etykietach. `StartTheQuiz()` zostanie ostatecznie wypełni wszystkie problemy, a następnie uruchomi timer, więc Dodaj komentarz. Funkcja powinna wyglądać następująco.

     [!code-csharp[VbExpressTutorial3Step2#3](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_3.cs)]
     [!code-vb[VbExpressTutorial3Step2#3](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_3.vb)]

     Należy zauważyć, że po wprowadzeniu kropki (.) po `randomizer` w kodzie okno technologii IntelliSense otwiera i wyświetla wszystkie metody obiektu Random, które można wywoływać. Na przykład, IntelliSense wyświetla `Next()` metody w następujący sposób.

     ![Następna metoda](../ide/media/express_randomwhite.png) Next — metoda

     Po wprowadzeniu kropkę po obiekcie, IntelliSense pokazuje listę członków obiektu, takie jak właściwości, metody i zdarzenia.

    > [!NOTE]
    >  Kiedy używasz `Next()` metody z `Random` obiektu, na przykład gdy wywołujesz `randomizer.Next(50)`, otrzymujesz losową liczbę, która jest mniejsza niż 50 (od 0 do 49). W tym przykładzie jest wywoływana `randomizer.Next(51)`. Użyto 51 zamiast 50, aby dwie liczby losowe spowoduje dodanie do odpowiedzi, który jest z zakresu od 0 do 100. W przypadku przekazania 50 do `Next()` metody, wybiera ona numer od 0 do 49, więc najwyższa możliwa odpowiedź to 98, a nie 100. Po uruchomieniu pierwszych dwóch instrukcji w metodzie, wszystkich zmiennych dwie liczby całkowitej, **addend1** i **addend2**, zawiera losową liczbę z zakresu od 0 do 50. Ten zrzut ekranu pokazuje kod Visual C#, ale technologia IntelliSense działa tak samo dla języka Visual Basic.

     Przyjrzyj się bliżej tych instrukcji.

     [!code-csharp[VbExpressTutorial3Step2#18](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_4.cs)]
     [!code-vb[VbExpressTutorial3Step2#18](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_4.vb)]

     Instrukcje ustawiają **tekstu** właściwości **plusLeftLabel** i **plusRightLabel** tak że wyświetlają one dwie liczby losowe. Należy użyć liczb całkowitych `ToString()` metodę, aby konwertować liczby na tekst. (W programowaniu ciąg oznacza tekst. Formanty etykiet wyświetlane tylko tekst, a nie liczby.

6.  W oknie projektu kliknij dwukrotnie **Start** przycisku, lub wybierz go, a następnie wybierz **Enter** klucza.

     Gdy uczestnik quizu wybierze ten przycisk, quiz powinien się rozpocząć, a właśnie dodałeś program obsługi zdarzeń kliknięcie, aby zaimplementować to zachowanie.

7.  Dodaj dwie poniższe instrukcje.

     [!code-csharp[VbExpressTutorial3Step2#4](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_5.cs)]
     [!code-vb[VbExpressTutorial3Step2#4](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_5.vb)]

     Pierwsza instrukcja wywołuje nową `StartTheQuiz()` metody. Druga instrukcja ustawia **włączone** właściwość **startButton** kontrolę **False** tak, aby osoba wypełniająca quiz nie może wybrać przycisku podczas quizu.

8.  Zapisz swój kod, uruchom go, a następnie wybierz **Start** przycisku.

     Problem losowego dodawania pojawi się, jak pokazano na następującym rysunku.

     ![Problem losowego dodawania](../ide/media/express_additionproblem.png) losowy problem dodawania

     W następnym kroku samouczka dodasz sumę.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 3: Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1: Tworzenie projektu i dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
