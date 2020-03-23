---
title: 'Krok 6: Dodaj problem odejmowania'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b6dd2b572074265cca62a45b962c604abf5c849
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579821"
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6: Dodaj problem odejmowania
W szóstej części tego samouczka dodasz problem z odejmowanie i dowiesz się, jak wykonać następujące zadania:

- Przechowuj wartości odejmowania.

- Wygeneruj losowe liczby dla problemu (i upewnij się, że odpowiedź wynosi od 0 do 100).

- Zaktualizuj metodę, która sprawdza odpowiedzi, tak aby sprawdzała również nowy problem odejmowania.

- Zaktualizuj <xref:System.Windows.Forms.Timer.Tick> program obsługi zdarzeń czasomierza, tak aby program obsługi zdarzeń wypełniał poprawną odpowiedź, gdy skończy się czas.

> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie quizu matematycznego z czasem](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-subtraction-problem"></a>Aby dodać problem z odejmowanie

1. Dodaj dwie zmienne całkowite dla problemu odejmowania do formularza między zmiennymi całkowitymi dla problemu dodawania a czasomierzem. Kod powinien wyglądać następująco.

     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Nazwy nowych zmiennych całkowitych —**minuend** i **subtrahend**— nie są terminami programowania. Są to tradycyjne nazwy w arytmetyce dla liczby, która jest odejmowana (subtrahend) i liczby, od której odejmowany jest subtrahend (minuend). Różnica jest minuend minus subtrahend. Można użyć innych nazw, ponieważ program nie wymaga określonych nazw zmiennych, formantów, składników lub metod. Należy przestrzegać reguł, takich jak nie uruchamianie nazw cyfr, ale zazwyczaj można używać nazw, takich jak x1, x2, x3 i x4. Jednak nazwy ogólne sprawiają, że kod jest trudny do odczytania i problemy prawie niemożliwe do wyśledzenia. Aby zachować nazwy zmiennych unikatowe i pomocne, użyjesz tradycyjnych nazw do mnożenia (multiplicand × mnożnik = produkt) i podziału (dywidenda ÷ dzielnik = iloraz) w dalszej części tego samouczka.

     Następnie zmodyfikujesz `StartTheQuiz()` metodę, aby zapewnić losowe wartości problemu odejmowania.

2. Dodaj następujący kod po komentarzu "Wypełnij problem odejmowania".

     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]

     Aby zapobiec negatywnym odpowiedziom na problem odejmowania, ten kod używa <xref:System.Random.Next> metody <xref:System.Random> klasy nieco inaczej niż problem z dodawaniem. Po podaniu `Next()` metody dwie wartości, wybiera liczbę losową, która jest większa lub równa pierwszej wartości i mniejsza niż druga. Poniższy kod wybiera liczbę losową od 1 do 100 i przechowuje ją w zmiennej minuend.

     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]

     Można wywołać `Next()` metodę Random klasy, który został nazwany "randomizer" wcześniej w tym samouczku, na wiele sposobów. Metody, które można wywołać w więcej niż jeden sposób są określane jako przeciążone i można użyć IntelliSense do ich eksplorowania. Spójrz ponownie na etykietkę narzędzia okna IntelliSense dla `Next()` metody.

     ![Etykietka narzędzia okna IntelliSense](../ide/media/express_overloads.png)<br/>
*Etykietka narzędzia okna* ***IntelliSense***

     Etykietka narzędzia pokazuje **(+ 2 przeciążenia(y))** `Next()` , co oznacza, że można wywołać metodę na dwa inne sposoby. Przeciążenia zawierają różne liczby lub typy argumentów, dzięki czemu działają nieco inaczej od siebie. Na przykład metoda może mieć pojedynczy argument liczby całkowitej, a jeden z jego przeciążenia może mieć liczbę całkowitą i ciąg. Możesz wybrać prawidłowe przeciążenie w zależności od tego, co chcesz zrobić. Po dodaniu kodu `StartTheQuiz()` do metody więcej informacji pojawia się w oknie IntelliSense zaraz po wprowadzeniu `randomizer.Next(`pliku . Aby przełączać się między przeciążeniami, wybierz klawisze **Strzałka** w górę i Strzałka w **dół,** jak pokazano na poniższej ilustracji:

     ![Przeciążenie dla metody Next&#40;&#41; w IntelliSense](../ide/media/express_nextoverload.png)<br/>
*Przeciążenie dla* metody ***Next()*** *w* ***intellisense***

     W takim przypadku chcesz wybrać ostatnie przeciążenie, ponieważ można określić wartości minimalne i maksymalne.

3. Zmodyfikuj metodę, `CheckTheAnswer()` aby sprawdzić, czy nie ma poprawnej odpowiedzi odejmowania.

     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]

     W języku `&&` C# `logical and` jest operatorem. W języku Visual Basic, `AndAlso`operatorem równoważnym jest . Te operatory wskazują "Jeśli suma addend1 i addend2 jest równa wartości sumy NumericUpDown i jeśli minuend minus subtrahend jest równa wartości różnicy NumericUpDown." Metoda `CheckTheAnswer()` zwraca `true` tylko wtedy, gdy odpowiedzi na dodawanie i problemy odejmowania są poprawne.

4. Zastąp ostatnią część programu obsługi zdarzeń tick czasomierza następującym kodem, aby wypełnił poprawną odpowiedź, gdy skończy się czas.

     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]

5. Zapisz i uruchom kod.

     Program zawiera problem z odejmowanie, jak pokazano na poniższej ilustracji:

     ![Quiz matematyczny z problemem odejmowania](../ide/media/express_addsubtract.png)<br/>
***Quiz matematyczny*** *z problemem odejmowania*

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 7: Dodawanie problemów z mnożeniem i dzieleniem](../ide/step-7-add-multiplication-and-division-problems.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 5: Dodawanie programów obsługi zdarzeń Enter dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
