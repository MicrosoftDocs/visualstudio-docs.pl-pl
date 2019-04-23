---
title: Krok 2. Tworzenie losowego problemu dodawania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 318caec1f96bc0b69a6fe9540231608a8636e107
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099503"
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2. Tworzenie zadania z dodawaniem losowych liczb
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W drugiej części tego samouczka należy quiz trudne, dodając zagadnienia matematyczne oparte na liczbach losowych. Możesz również utworzyć metodę, która nosi nazwę `StartTheQuiz()` i który wypełnia ona problemy i uruchamia minutnik. W dalszej części tego samouczka dodasz odejmowania, mnożenia i dzielenia problemów.  
  
> [!NOTE]
>  Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby uzyskać omówienie samouczka, zobacz [samouczek 2: Utwórz Quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-create-a-random-addition-problem"></a>Aby utworzyć losowy problem dodawania  
  
1. W Projektancie formularza wybierz formularz (formularz Form1).  
  
2. Na pasku menu wybierz **widoku**, **kodu**.  
  
     Form1.CS lub Form1.vb pojawia się, w zależności od języka programowania, którego używasz, dzięki czemu można wyświetlić kod związany z formularzem.  
  
3. Tworzenie `Random` obiekt poprzez dodanie `new` instrukcji w górnej części kodu, podobnie do poniższego.  
  
     [!code-csharp[VbExpressTutorial3Step2#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial3Step2#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#1)]  
  
     Po dodaniu `Random` obiektu do formularza i nadano **randomizer**.  
  
     `Random` jest znany jako obiekt. Prawdopodobnie słyszałeś już słowo, i Dowiedz się więcej na temat co to oznacza dla programowania w następnym samouczku. Teraz wystarczy pamiętać, że można użyć `new` instrukcji, aby utworzyć przyciski, etykiety, panele, okna Openfiledialog, Colordialog, SoundPlayer, Random i nawet formularze i te elementy są określane jako obiekty. Jeśli uruchamiasz program, formularz zostaje uruchomiony i tworzy kod związany z nim `Random` obiektu i nadaje mu **randomizer**.  
  
     Wkrótce będziesz tworzyć metodę sprawdzania odpowiedzi, dlatego quiz musi używać zmiennych do przechowywania liczb losowych, który generuje dla każdego problemu. Zobacz [zmienne](http://msdn.microsoft.com/library/4cfaa06d-4ae3-4307-897b-cf599dc24caa) lub [typy](http://msdn.microsoft.com/library/f782d7cc-035e-4500-b1b1-36a9881130ad). Aby prawidłowo używać zmiennych, musisz je zadeklarować, co oznacza utworzenie listy ich nazwy i typy danych.  
  
4. Dodaj dwie zmienne liczby całkowitej do formularza i nazwij je **addend1** i **addend2**.  
  
    > [!NOTE]
    >  Zmienną całkowitą jest znana jako int w języku C# lub liczba całkowita w języku Visual Basic. Tego typu zmienna przechowuje liczbę dodatnią lub ujemną od -2147483648 do 2147483647 i może przechowywać jedynie liczby całkowite, nie miejsca po przecinku.  
  
     Użyj podobnej składni, aby dodać zmienną całkowitą, jak dodać `Random` obiektu, co ilustruje poniższy kod.  
  
     [!code-csharp[VbExpressTutorial3Step2#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial3Step2#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#2)]  
  
5. Dodaj metodę o nazwie `StartTheQuiz()` i który korzysta `Random` obiektu `Next()` metodę do pokazania liczb losowych w etykietach. `StartTheQuiz()` zostanie ostatecznie wypełni wszystkie problemy, a następnie uruchomi timer, więc Dodaj komentarz. Funkcja powinna wyglądać następująco.  
  
     [!code-csharp[VbExpressTutorial3Step2#3](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#3)]
     [!code-vb[VbExpressTutorial3Step2#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#3)]  
  
     Należy zauważyć, że po wprowadzeniu kropki (.) po **randomizer** w kodzie okno technologii IntelliSense otwiera i pokazuje wszystkie `Random` metody obiektu, które można wywoływać. Na przykład, Intellisense Wyświetla `Next()` metody w następujący sposób.  
  
     ![Następna metoda](../ide/media/express-randomwhite.png "Express_RandomWhite")  
Next — metoda  
  
     Po wprowadzeniu kropkę po obiekcie, IntelliSense pokazuje listę członków obiektu, takie jak właściwości, metody i zdarzenia.  
  
    > [!NOTE]
    >  Kiedy używasz `Next()` metody z `Random` obiektu, na przykład gdy wywołujesz `randomizer.Next(50)`, otrzymujesz losową liczbę, która jest mniejsza niż 50 (od 0 do 49). W tym przykładzie jest wywoływana `randomizer.Next(51)`. Użyto 51 zamiast 50, aby dwie liczby losowe spowoduje dodanie do odpowiedzi, który jest z zakresu od 0 do 100. W przypadku przekazania 50 do `Next()` metody, wybiera ona numer od 0 do 49, więc najwyższa możliwa odpowiedź to 98, a nie 100. Po uruchomieniu pierwszych dwóch instrukcji w metodzie, wszystkich zmiennych dwie liczby całkowitej, `addend1` i `addend2`, zawiera losową liczbę z zakresu od 0 do 50. Ten zrzut ekranu pokazuje kod Visual C#, ale technologia IntelliSense działa tak samo dla języka Visual Basic.  
  
     Przyjrzyj się bliżej tych instrukcji.  
  
     [!code-csharp[VbExpressTutorial3Step2#18](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#18)]
     [!code-vb[VbExpressTutorial3Step2#18](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#18)]  
  
     Instrukcje ustawiają **tekstu** właściwości **plusLeftLabel** i **plusRightLabel** tak że wyświetlają one dwie liczby losowe. Należy użyć liczb całkowitych `ToString()` metodę, aby konwertować liczby na tekst. (W programowaniu ciąg oznacza tekst. Formanty etykiet wyświetlane tylko tekst, a nie liczby.  
  
6. W oknie projektu kliknij dwukrotnie **Start** przycisku, lub wybierz ją, a następnie naciśnij klawisz Enter.  
  
     Gdy uczestnik quizu wybierze ten przycisk, quiz powinien się rozpocząć, a właśnie dodałeś program obsługi zdarzeń kliknięcie, aby zaimplementować to zachowanie.  
  
7. Dodaj dwie poniższe instrukcje.  
  
     [!code-csharp[VbExpressTutorial3Step2#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial3Step2#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#4)]  
  
     Pierwsza instrukcja wywołuje nową `StartTheQuiz()` metody. Druga instrukcja ustawia **włączone** właściwość **startButton** kontrolę **False** tak, aby osoba wypełniająca quiz nie może wybrać przycisku podczas quizu.  
  
8. Zapisz swój kod, uruchom go, a następnie wybierz **Start** przycisku.  
  
     Problem losowego dodawania pojawi się, jak pokazano na następującym rysunku.  
  
     ![Problem losowego dodawania](../ide/media/express-additionproblem.png "Express_AdditionProblem")  
Problem losowego dodawania  
  
     W następnym kroku samouczka dodasz sumę.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Aby przejść do następnego kroku samouczka, zobacz [krok 3: Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md).  
  
- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1: Tworzenie projektu i dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
