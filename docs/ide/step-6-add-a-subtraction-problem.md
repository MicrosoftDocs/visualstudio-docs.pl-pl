---
title: Krok 6. Dodawanie problemu odejmowania
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6eb94423150a8a3a43183020ee87d52494355aed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996649"
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6. Dodawanie problemu odejmowania
W szóstej części tego samouczka dodasz problem odejmowania i Dowiedz się, jak wykonywać następujące zadania:

- Store wartości odejmowania.

- Wygeneruj liczby losowe dla problemu (i należy się upewnić, że odpowiedź na pytanie od 0 do 100).

- Zaktualizuj metodę, która sprawdza odpowiedzi, tak aby sprawdzała zbyt nowy problem odejmowania.

- Zaktualizuj swoje czasomierza <xref:System.Windows.Forms.Timer.Tick> program obsługi zdarzeń, aby obsługi zdarzeń wypełniał poprawną odpowiedź, gdy skończy się czas.

## <a name="to-add-a-subtraction-problem"></a>Aby dodać problem odejmowania

1. Dodawanie dwóch zmiennych całkowitych dla problemu odejmowania do formularza, między zmiennych całkowitych dla problemu dodawania oraz czasomierzem. Kod powinien wyglądać następująco.

     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]

     Nazwy nowych zmiennych całkowitych —**odjemna** i **odjemnik**— nie terminy programistyczne. Są to tradycyjne nazwy stosowane w operacjach arytmetycznych dla liczby, która jest odejmowana (odjemnik) i liczby, od której odjemnik jest odejmowany (odjemna). Różnica to odjemna minus odjemnik. Można użyć innych nazw, ponieważ Twój program nie wymaga określonych nazw zmiennych, formantów, składników lub metody. Należy przestrzegać reguł, takich jak nazw od cyfr, ale zazwyczaj można użyć nazwy, takie jak x1, x2, x3 i x4. Jednak nazwy rodzajowe wprowadzać czytelność kodu i problemów śledzenie jest prawie niemożliwe. Aby zachować nazwy zmiennych, unikatowe i pomocne, użyjesz to tradycyjne nazwy stosowane dla mnożenia (którą mnożona jest mnożna × mnożnik = produkt) i dzielenia (dzielnik ÷ dzielna = iloraz) później w tym samouczku.

     Następnie zmodyfikujesz `StartTheQuiz()` metodę, aby dostarczyć losowe wartości dla problemu odejmowania.

2. Dodaj następujący kod po komentarzu "Wypełnij problem odejmowania".

     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]

     Aby uniemożliwić ujemne odpowiedzi dla problemu odejmowania, ten kod używa <xref:System.Random.Next> metody <xref:System.Random> nieco klasy inaczej od jak odbywa się na problem dodawania. Kiedy nadasz `Next()` metoda dwie wartości, wybiera liczbę losową, która jest większa niż lub równa pierwszej wartości i mniejsza niż ten drugi. Poniższy kod wybiera losową liczbę z zakresu od 1 do 100 i zapisuje ją w zmiennej odjemna.

     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]

     Możesz wywołać `Next()` metody klasy Random nosi nazwę "randomizer" wcześniej w tym samouczku na wiele sposobów. Metody, które można wywołać w więcej niż jeden sposób, są określane jako przeciążone, a następnie korzystać z technologii IntelliSense, aby zapoznać się z nimi. Ponownie Przyjrzyj się etykietka narzędzia okna technologii IntelliSense dla `Next()` metody.

     ![Etykietka narzędzia okna technologii IntelliSense](../ide/media/express_overloads.png)
**IntelliSense** etykietka narzędzia okna

     Etykietka narzędzia pokazuje **(+ 2 overload(s))** , co oznacza, że można wywołać `Next()` metody na dwa inne sposoby. Przeciążenia zawierają różną liczbę lub typy argumentów, tak że każde działa nieco inaczej od siebie nawzajem. Na przykład metoda może przyjmować jeden argument, a jeden z jej przeciążeń może być liczbą całkowitą i ciąg. Możesz wybrać poprawne przeciążenie oparte na co chcesz zrobić. Po dodaniu kod, aby `StartTheQuiz()` metody, więcej informacji znajduje się w oknie technologii IntelliSense zaraz po wprowadzeniu `randomizer.Next(`. Aby przechodzić między przeciążeniami, wybierz opcję **Strzałka w górę** i **strzałkę w dół** klucze, jak pokazano na poniższej ilustracji:

     ![Przeciążenie dla następnego&#40; &#41; metody w technologii IntelliSense](../ide/media/express_nextoverload.png) przeciążenia dla **Next()** method in Class metoda **IntelliSense**

     W tym przypadku chcesz wybrać ostatnie przeciążenie, ponieważ można określić wartości minimalne i maksymalne.

3. Modyfikowanie `CheckTheAnswer()` metodę sprawdzania, czy poprawną odpowiedź odejmowania.

     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]

     W języku Visual C# `&&` jest `logical and` operatora. W języku Visual Basic, równorzędny operator to `AndAlso`. Te operatory wskazują "Jeśli suma addend1 i addend2 jest równa wartości sumy NumericUpDown i jeśli odjemna minus odjemnik jest równa wartości różnicy NumericUpDown." `CheckTheAnswer()` Metoda zwraca `true` tylko wtedy, gdy odpowiedzi na dodawanie i problemy odejmowania są poprawne.

4. Zastąp ostatnią część programu obsługi zdarzeń Tick timera następującym kodem, tak aby wypełnił poprawną odpowiedź, gdy skończy się czas.

     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]

5. Zapisz i uruchom kod.

     Program obejmuje problem odejmowania, jak pokazano na następującym rysunku:

     ![Quiz matematyczny z problemem odejmowania](../ide/media/express_addsubtract.png)
**kwizu matematycznego z limitem** z problemem odejmowania

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [kroku 7: Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5: Dodawanie obsługi zdarzeń Enter dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
