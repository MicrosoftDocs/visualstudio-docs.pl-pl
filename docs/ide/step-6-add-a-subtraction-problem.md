---
title: Krok 6. Dodawanie zadania z odejmowaniem
description: Dowiedz się, jak dodać problem odejmowania, a także dowiedzieć się, jak wykonywać zadania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 511158cba039f83cadcb469511eb24fdd58375b1
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296342"
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6. Dodawanie zadania z odejmowaniem
W szóstej części tego samouczka dodasz problem odejmowania i dowiesz się, jak wykonywać następujące zadania:

- Zapisz wartości odejmowania.

- Generuj liczby losowe dla problemu (i upewnij się, że odpowiedź należy do zakresu od 0 do 100).

- Zaktualizuj metodę, która sprawdza odpowiedzi, aby sprawdzić, czy jest to również nowy problem odejmowania.

- Zaktualizuj <xref:System.Windows.Forms.Timer.Tick> procedurę obsługi zdarzeń czasomierza, tak aby program obsługi zdarzeń wypełniał poprawną odpowiedź, gdy skończy się czas.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-subtraction-problem"></a>Aby dodać problem odejmowania

1. Dodaj dwie zmienne całkowite dla problemu odejmowania do formularza, między zmiennymi całkowitymi dla problemu dodawania i czasomierzem. Kod powinien wyglądać podobnie do poniższego.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet12":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Nazwy nowych zmiennych liczb całkowitych —**odjemna** i **odjemnik**— nie są terminami programowania. Są to tradycyjne nazwy arytmetyczne dla liczby, która jest odejmowana (odjemnik) i liczba, z której jest odejmowany odjemnik (odjemna). Różnica to odjemna minus odjemnik. Można użyć innych nazw, ponieważ program nie wymaga określonych nazw dla zmiennych, formantów, składników lub metod. Należy przestrzegać reguł, takich jak nierozpoczynanie nazw z cyframi, ale zazwyczaj można używać nazw takich jak x1, X2, x3 i x4. Jednak nazwy ogólne utrudniają odczytywanie i rozwiązywanie problemów niemal niemożliwe do śledzenia. Aby zachować unikatową i użyteczność nazw zmiennych, należy użyć tradycyjnych nazw dla mnożenia (multiplicand × mnożnik = Product) i dzielenia (dzielną ÷ dzielnik = iloraz) w dalszej części tego samouczka.

     Następnie zmodyfikujesz `StartTheQuiz()` metodę, aby zapewnić losowe wartości problemu odejmowania.

2. Dodaj następujący kod po komentarzu "Wypełnij problem odejmowania".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet13":::

     Aby zapobiec negatywnej odpowiedzi na problem odejmowania, ten kod używa <xref:System.Random.Next> metody <xref:System.Random> klasy a nieco inaczej niż w przypadku problemu z dodawaniem. Po nadaniu `Next()` metodu dwie wartości wybierają liczbę losową, która jest większa lub równa pierwszej wartości i mniejsza od drugiej. Poniższy kod wybiera liczbę losową z przestawu od 1 do 100 i zapisuje ją w zmiennej odjemna.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet21":::

     Można wywołać `Next()` metodę klasy losowej o nazwie "randomer" wcześniej w tym samouczku, na wiele sposobów. Metody, które można wywołać w więcej niż jednym sposobie, są określane jako przeciążone i można użyć funkcji IntelliSense, aby poznać ją. Ponownie Obejrzyj etykietkę narzędzia okna IntelliSense dla `Next()` metody.

     ![Etykietka narzędzia okna IntelliSense](../ide/media/express_overloads.png)<br/>
***IntelliSense** _ _window etykietka narzędzia *

     Etykietka narzędzia pokazuje **(+ 2 przeciążenia**), co oznacza, że można wywołać `Next()` metodę na dwa inne sposoby. Przeciążenia zawierają różne liczby lub typy argumentów, dzięki czemu działają nieco inaczej od siebie. Na przykład metoda może przyjmować jeden argument Integer, a jedno z jego przeciążeń może przyjmować liczbę całkowitą i ciąg. Należy wybrać poprawne Przeciążenie w zależności od tego, co ma być wykonywane. Po dodaniu kodu do `StartTheQuiz()` metody w oknie IntelliSense pojawiają się dodatkowe informacje, które wkrótce wprowadzisz `randomizer.Next(` . Aby przechodzić przez przeciążenia, wybierz klawisze **Strzałka w górę** i **Strzałka w dół** , jak pokazano na poniższej ilustracji:

     ![Przeciążenie metody Next&#40;&#41; w technologii IntelliSense](../ide/media/express_nextoverload.png)<br/>
*Przeciążenie dla*  * **Next ()** _ _method in * ***IntelliSense***

     W takim przypadku należy wybrać ostatnie Przeciążenie, ponieważ można określić wartości minimalne i maksymalne.

3. Zmodyfikuj `CheckTheAnswer()` metodę, aby sprawdzić poprawność odejmowania.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet14":::

     W języku C# `&&` jest `logical and` operatorem. W Visual Basic, odpowiednik operatora to `AndAlso` . Te operatory wskazują, czy suma addend1 i addend2 jest równa wartości sumy NumericUpDown i jeśli odjemna minus odjemnik jest równa wartości różnicy NumericUpDown ". `CheckTheAnswer()`Metoda zwraca `true` tylko wtedy, gdy odpowiedzi na dodanie i problemy z odejmowaniem są poprawne.

4. Zamień ostatnią część programu obsługi zdarzeń taktu czasomierza na następujący kod, tak aby wypełniał poprawną odpowiedź, gdy skończy się czas.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet22":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet22":::

5. Zapisz i Uruchom swój kod.

     Program zawiera problem odejmowania, jak pokazano na poniższej ilustracji:

     ![Quiz matematyczny z problemem odejmowania](../ide/media/express_addsubtract.png)<br/>
***Quiz matematyczny** _ _with problem odejmowania *

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 7: Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5. Dodawanie obsługi zdarzeń wprowadzania dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
