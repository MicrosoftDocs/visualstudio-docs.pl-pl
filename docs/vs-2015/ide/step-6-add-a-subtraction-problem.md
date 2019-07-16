---
title: Krok 6. Dodawanie problemu odejmowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e846bc8dc8d3087c58d58ee91752abc713c5f66e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178676"
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6. Dodawanie zadania z odejmowaniem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W szóstej części tego samouczka dodasz problem odejmowania i Dowiedz się, jak wykonywać następujące zadania:  
  
- Store wartości odejmowania.  
  
- Wygeneruj liczby losowe dla problemu (i należy się upewnić, że odpowiedź na pytanie od 0 do 100).  
  
- Zaktualizuj metodę, która sprawdza odpowiedzi, tak aby sprawdzała zbyt nowy problem odejmowania.  
  
- Zaktualizować programu obsługi zdarzeń Tick czasomierza usługi obsługi zdarzeń wypełniał poprawną odpowiedź, gdy skończy się czas.  
  
### <a name="to-add-a-subtraction-problem"></a>Aby dodać problem odejmowania  
  
1. Dodawanie dwóch zmiennych całkowitych dla problemu odejmowania do formularza, między zmiennych całkowitych dla problemu dodawania oraz czasomierzem. Kod powinien wyglądać następująco.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#12](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#12)]
     [!code-vb[VbExpressTutorial3Step5_6#12](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#12)]  
  
     Nazwy nowych zmiennych całkowitych —**odjemna** i **odjemnik**— nie terminy programistyczne. Są to tradycyjne nazwy stosowane w operacjach arytmetycznych dla liczby, która jest odejmowana (odjemnik) i liczby, od której odjemnik jest odejmowany (odjemna). Różnica to odjemna minus odjemnik. Można użyć innych nazw, ponieważ Twój program nie wymaga określonych nazw zmiennych, formantów, składników lub metody. Należy przestrzegać reguł, takich jak nazw od cyfr, ale zazwyczaj można użyć nazwy, takie jak x1, x2, x3 i x4. Jednak nazwy rodzajowe wprowadzać czytelność kodu i problemów śledzenie jest prawie niemożliwe. Aby zachować nazwy zmiennych, unikatowe i pomocne, użyjesz to tradycyjne nazwy stosowane dla mnożenia (którą mnożona jest mnożna × mnożnik = produkt) i dzielenia (dzielnik ÷ dzielna = iloraz) później w tym samouczku.  
  
     Następnie zmodyfikujesz `StartTheQuiz()` metodę, aby dostarczyć losowe wartości dla problemu odejmowania.  
  
2. Dodaj następujący kod po komentarzu "Wypełnij problem odejmowania".  
  
     [!code-csharp[VbExpressTutorial3Step5_6#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#13)]
     [!code-vb[VbExpressTutorial3Step5_6#13](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#13)]  
  
     Aby uniemożliwić ujemne odpowiedzi dla problemu odejmowania, ten kod używa `Next()` metody `Random` nieco klasy inaczej od jak odbywa się na problem dodawania. Kiedy nadasz `Next()` metoda dwie wartości, wybiera liczbę losową, która jest większa niż lub równa pierwszej wartości i mniejsza niż ten drugi. Poniższy kod wybiera losową liczbę z zakresu od 1 do 100 i zapisuje ją w zmiennej odjemna.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#21](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#21)]
     [!code-vb[VbExpressTutorial3Step5_6#21](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#21)]  
  
     Możesz wywołać `Next()` metody `Random` klasy, która nosi nazwę "randomizer" wcześniej w tym samouczku na wiele sposobów. Metody, które można wywołać w więcej niż jeden sposób, są określane jako przeciążone, a następnie korzystać z technologii IntelliSense, aby zapoznać się z nimi. Ponownie Przyjrzyj się etykietka narzędzia okna technologii IntelliSense dla `Next()` metody.  
  
     ![Etykietka narzędzia okna technologii IntelliSense](../ide/media/express-overloads.png "Express_Overloads")  
Etykietka narzędzia okna technologii IntelliSense  
  
     Etykietka narzędzia pokazuje **(+ 2 overload(s))** , co oznacza, że można wywołać `Next()` metody na dwa inne sposoby. Przeciążenia zawierają różną liczbę lub typy argumentów, tak że każde działa nieco inaczej od siebie nawzajem. Na przykład metoda może przyjmować jeden argument, jeden z jej przeciążeń może stać się liczba całkowita i ciąg. Możesz wybrać poprawne przeciążenie oparte na co chcesz zrobić. Po dodaniu kod, aby `StartTheQuiz()` metody, więcej informacji znajduje się w oknie technologii Intellisense zaraz po wprowadzeniu `randomizer.Next(`. Wybierz klawisze strzałki w górę i Strzałka w dół, aby przechodzić między przeciążeniami, jak pokazano na następującym rysunku.  
  
     ![Przeciążenie dla następnego&#40; &#41; metody w technologii IntelliSense](../ide/media/express-nextoverload.png "Express_NextOverload")  
Przeciążenie dla metody Next() w technologii IntelliSense  
  
     W tym przypadku chcesz wybrać ostatnie przeciążenie, ponieważ można określić wartości minimalne i maksymalne.  
  
3. Modyfikowanie `CheckTheAnswer()` metodę sprawdzania, czy poprawną odpowiedź odejmowania.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial3Step5_6#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#14)]  
  
     W języku Visual C# `&&` jest `logical and` operatora. W języku Visual Basic, równorzędny operator to `AndAlso`. Te operatory wskazują "Jeśli suma addend1 i addend2 jest równa wartości sumy NumericUpDown i jeśli odjemna minus odjemnik jest równa wartości różnicy NumericUpDown." `CheckTheAnswer()` Metoda zwraca `true` tylko wtedy, gdy odpowiedzi na dodawanie i problemy odejmowania są poprawne.  
  
4. Zastąp ostatnią część programu obsługi zdarzeń Tick timera następującym kodem, tak aby wypełnił poprawną odpowiedź, gdy skończy się czas.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#22](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#22)]
     [!code-vb[VbExpressTutorial3Step5_6#22](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#22)]  
  
5. Zapisz i uruchom kod.  
  
     Program obejmuje problem odejmowania, jak pokazano na następującym rysunku.  
  
     ![Quiz matematyczny z problemem odejmowania](../ide/media/express-addsubtract.png "Express_AddSubtract")  
Quiz matematyczny z problemem odejmowania  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Aby przejść do następnego kroku samouczka, zobacz [kroku 7: Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).  
  
- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5: Dodawanie obsługi zdarzeń wprowadzania dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
