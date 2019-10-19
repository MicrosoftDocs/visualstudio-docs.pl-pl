---
title: Krok 6. Dodawanie problemu odejmowania
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4789248a129bcd41452af1184418f9f59ede7595
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562574"
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6. Dodawanie problemu odejmowania
W szóstej części tego samouczka dodasz problem odejmowania i dowiesz się, jak wykonywać następujące zadania:

- Zapisz wartości odejmowania.

- Generuj liczby losowe dla problemu (i upewnij się, że odpowiedź należy do zakresu od 0 do 100).

- Zaktualizuj metodę, która sprawdza odpowiedzi, aby sprawdzić, czy jest to również nowy problem odejmowania.

- Zaktualizuj <xref:System.Windows.Forms.Timer.Tick> obsługi zdarzeń czasomierza, tak aby program obsługi zdarzeń wypełniał poprawną odpowiedź, gdy zostanie przekroczony czas.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem.
> - Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Aby pobrać kompletną wersję kodu, zobacz [kompletny przykładowy samouczek quizu Matematycznego](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-add-a-subtraction-problem"></a>Aby dodać problem odejmowania

1. Dodaj dwie zmienne całkowite dla problemu odejmowania do formularza, między zmiennymi całkowitymi dla problemu dodawania i czasomierzem. Kod powinien wyglądać podobnie do poniższego.

     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Nazwy nowych zmiennych liczb całkowitych —**odjemna** i **odjemnik**— nie są terminami programowania. Są to tradycyjne nazwy arytmetyczne dla liczby, która jest odejmowana (odjemnik) i liczba, z której jest odejmowany odjemnik (odjemna). Różnica to odjemna minus odjemnik. Można użyć innych nazw, ponieważ program nie wymaga określonych nazw dla zmiennych, formantów, składników lub metod. Należy przestrzegać reguł, takich jak nierozpoczynanie nazw z cyframi, ale zazwyczaj można używać nazw takich jak x1, X2, x3 i x4. Jednak nazwy ogólne utrudniają odczytywanie i rozwiązywanie problemów niemal niemożliwe do śledzenia. Aby zachować unikatową i użyteczność nazw zmiennych, należy użyć tradycyjnych nazw dla mnożenia (multiplicand × mnożnik = Product) i dzielenia (dzielną ÷ dzielnik = iloraz) w dalszej części tego samouczka.

     Następnie zmodyfikujesz metodę `StartTheQuiz()`, aby zapewnić losowe wartości problemu odejmowania.

2. Dodaj następujący kod po komentarzu "Wypełnij problem odejmowania".

     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]

     Aby zapobiec negatywnej odpowiedzi na problem odejmowania, ten kod używa metody <xref:System.Random.Next> klasy <xref:System.Random> a nieco inaczej niż w przypadku problemu z dodawaniem. Po nadaniu metody `Next()` dwie wartości wybierają liczbę losową, która jest większa lub równa pierwszej wartości i mniejsza od drugiej. Poniższy kod wybiera liczbę losową z przestawu od 1 do 100 i zapisuje ją w zmiennej odjemna.

     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]

     Można wywołać metodę `Next()` klasy losowej o nazwie "Randomer" wcześniej w tym samouczku, na wiele sposobów. Metody, które można wywołać w więcej niż jednym sposobie, są określane jako przeciążone i można użyć funkcji IntelliSense, aby poznać ją. Ponownie Obejrzyj etykietkę narzędzia okna IntelliSense dla metody `Next()`.

     ![IntelliSense etykietki narzędzia okna ](../ide/media/express_overloads.png)<br/>
*Etykietka narzędzia okna* IntelliSense

     Etykietka narzędzia pokazuje **(+ 2 przeciążenia**), co oznacza, że można wywołać metodę `Next()` na dwa inne sposoby. Przeciążenia zawierają różne liczby lub typy argumentów, dzięki czemu działają nieco inaczej od siebie. Na przykład metoda może przyjmować jeden argument Integer, a jedno z jego przeciążeń może przyjmować liczbę całkowitą i ciąg. Należy wybrać poprawne Przeciążenie w zależności od tego, co ma być wykonywane. Po dodaniu kodu do metody `StartTheQuiz()` więcej informacji pojawia się w oknie IntelliSense, gdy tylko wprowadzisz pozycję `randomizer.Next(`. Aby przechodzić przez przeciążenia, wybierz klawisze **Strzałka w górę** i **Strzałka w dół** , jak pokazano na poniższej ilustracji:

     ![Overload dla następnej&#40; &#41; metody IntelliSense ](../ide/media/express_nextoverload.png)<br/>
*Przeciążenie* metody ***Next ()*** *w* ***technologii IntelliSense***

     W takim przypadku należy wybrać ostatnie Przeciążenie, ponieważ można określić wartości minimalne i maksymalne.

3. Zmodyfikuj metodę `CheckTheAnswer()`, aby sprawdzić poprawność odejmowania.

     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]

     W C#programie `&&` jest operatorem `logical and`. W Visual Basic, odpowiednik operatora jest `AndAlso`. Te operatory wskazują, czy suma addend1 i addend2 jest równa wartości sumy NumericUpDown i jeśli odjemna minus odjemnik jest równa wartości różnicy NumericUpDown ". Metoda `CheckTheAnswer()` zwraca `true` tylko wtedy, gdy odpowiedzi na dodawanie i usuwanie problemów są poprawne.

4. Zamień ostatnią część programu obsługi zdarzeń taktu czasomierza na następujący kod, tak aby wypełniał poprawną odpowiedź, gdy skończy się czas.

     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]

5. Zapisz i Uruchom swój kod.

     Program zawiera problem odejmowania, jak pokazano na poniższej ilustracji:

     ![Math Quiz z problemem odejmowania ](../ide/media/express_addsubtract.png)<br/>
***Quiz matematyczny*** *z problemem odejmowania*

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 7: Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md)** .

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5. Dodawanie obsługi zdarzeń wprowadzania dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
