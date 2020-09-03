---
title: Krok 6. Dodawanie problemu odejmowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ec0bdd3ebae52158c5631a880e63ee0f3a455de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671713"
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6. Dodawanie problemu odejmowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W szóstej części tego samouczka dodasz problem odejmowania i dowiesz się, jak wykonywać następujące zadania:

- Zapisz wartości odejmowania.

- Generuj liczby losowe dla problemu (i upewnij się, że odpowiedź należy do zakresu od 0 do 100).

- Zaktualizuj metodę, która sprawdza odpowiedzi, aby sprawdzić, czy jest to również nowy problem odejmowania.

- Zaktualizuj procedurę obsługi zdarzeń taktowania czasomierza, tak aby program obsługi zdarzeń wypełniał poprawną odpowiedź, gdy zostanie przekroczony czas.

### <a name="to-add-a-subtraction-problem"></a>Aby dodać problem odejmowania

1. Dodaj dwie zmienne całkowite dla problemu odejmowania do formularza, między zmiennymi całkowitymi dla problemu dodawania i czasomierzem. Kod powinien wyglądać podobnie do poniższego.

     [!code-csharp[VbExpressTutorial3Step5_6#12](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#12)]
     [!code-vb[VbExpressTutorial3Step5_6#12](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#12)]

     Nazwy nowych zmiennych liczb całkowitych —**odjemna** i **odjemnik**— nie są terminami programowania. Są to tradycyjne nazwy arytmetyczne dla liczby, która jest odejmowana (odjemnik) i liczba, z której jest odejmowany odjemnik (odjemna). Różnica to odjemna minus odjemnik. Można użyć innych nazw, ponieważ program nie wymaga określonych nazw dla zmiennych, formantów, składników lub metod. Należy przestrzegać reguł, takich jak nierozpoczynanie nazw z cyframi, ale zazwyczaj można używać nazw takich jak x1, X2, x3 i x4. Jednak nazwy ogólne utrudniają odczytywanie i rozwiązywanie problemów niemal niemożliwe do śledzenia. Aby zachować unikatową i użyteczność nazw zmiennych, należy użyć tradycyjnych nazw dla mnożenia (multiplicand × mnożnik = Product) i dzielenia (dzielną ÷ dzielnik = iloraz) w dalszej części tego samouczka.

     Następnie zmodyfikujesz `StartTheQuiz()` metodę, aby zapewnić losowe wartości problemu odejmowania.

2. Dodaj następujący kod po komentarzu "Wypełnij problem odejmowania".

     [!code-csharp[VbExpressTutorial3Step5_6#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#13)]
     [!code-vb[VbExpressTutorial3Step5_6#13](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#13)]

     Aby zapobiec negatywnej odpowiedzi na problem odejmowania, ten kod używa `Next()` metody `Random` klasy a nieco inaczej niż w przypadku problemu z dodawaniem. Po nadaniu `Next()` metodu dwie wartości wybierają liczbę losową, która jest większa lub równa pierwszej wartości i mniejsza od drugiej. Poniższy kod wybiera liczbę losową z przestawu od 1 do 100 i zapisuje ją w zmiennej odjemna.

     [!code-csharp[VbExpressTutorial3Step5_6#21](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#21)]
     [!code-vb[VbExpressTutorial3Step5_6#21](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#21)]

     Można wywołać `Next()` metodę `Random` klasy o nazwie "losowo" w tym samouczku, na wiele sposobów. Metody, które można wywołać w więcej niż jednym sposobie, są określane jako przeciążone i można użyć funkcji IntelliSense, aby poznać ją. Ponownie Obejrzyj etykietkę narzędzia okna IntelliSense dla `Next()` metody.

     ![Etykietka narzędzia okna IntelliSense](../ide/media/express-overloads.png "Express_Overloads") Etykietka narzędzia okna IntelliSense

     Etykietka narzędzia pokazuje **(+ 2 przeciążenia**), co oznacza, że można wywołać `Next()` metodę na dwa inne sposoby. Przeciążenia zawierają różne liczby lub typy argumentów, dzięki czemu działają nieco inaczej od siebie. Na przykład metoda może przyjmować jeden argument Integer, podczas gdy jedno z jego przeciążeń może przyjmować liczbę całkowitą i ciąg. Należy wybrać poprawne Przeciążenie w zależności od tego, co ma być wykonywane. Po dodaniu kodu do `StartTheQuiz()` metody w oknie IntelliSense pojawiają się dodatkowe informacje, które wkrótce wprowadzisz `randomizer.Next(` . Wybierz klawisze STRZAŁKA w górę i Strzałka w dół, aby przechodzić przez przeciążenia, jak pokazano na poniższej ilustracji.

     ![Przeciążenie metody Next&#40;&#41; w technologii IntelliSense](../ide/media/express-nextoverload.png "Express_NextOverload") Przeciążenie metody Next () w technologii IntelliSense

     W takim przypadku należy wybrać ostatnie Przeciążenie, ponieważ można określić wartości minimalne i maksymalne.

3. Zmodyfikuj `CheckTheAnswer()` metodę, aby sprawdzić poprawność odejmowania.

     [!code-csharp[VbExpressTutorial3Step5_6#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial3Step5_6#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#14)]

     W języku Visual C# `&&` jest `logical and` operatorem. W Visual Basic, odpowiednik operatora to `AndAlso` . Te operatory wskazują, czy suma addend1 i addend2 jest równa wartości sumy NumericUpDown i jeśli odjemna minus odjemnik jest równa wartości różnicy NumericUpDown ". `CheckTheAnswer()`Metoda zwraca `true` tylko wtedy, gdy odpowiedzi na dodanie i problemy z odejmowaniem są poprawne.

4. Zamień ostatnią część programu obsługi zdarzeń taktu czasomierza na następujący kod, tak aby wypełniał poprawną odpowiedź, gdy skończy się czas.

     [!code-csharp[VbExpressTutorial3Step5_6#22](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#22)]
     [!code-vb[VbExpressTutorial3Step5_6#22](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#22)]

5. Zapisz i Uruchom swój kod.

     Program zawiera problem odejmowania, jak pokazano na poniższej ilustracji.

     ![Quiz matematyczny z problemem odejmowania](../ide/media/express-addsubtract.png "Express_AddSubtract") Quiz matematyczny z problemem odejmowania

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 7: Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5. Dodawanie obsługi zdarzeń wprowadzania dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
