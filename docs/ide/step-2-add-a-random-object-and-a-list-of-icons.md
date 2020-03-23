---
title: 'Krok 2: Dodaj losowy obiekt i listę ikon'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f4731778ebb3acbdc3bb7d9b5827c1015541d98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579419"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Krok 2: Dodaj losowy obiekt i listę ikon

W tym kroku utworzysz zestaw pasujących symboli dla gry. Każdy symbol jest dodawany do dwóch losowych komórek w TableLayoutPanel na formularzu. Aby to zrobić, `new` należy użyć dwóch instrukcji do utworzenia dwóch obiektów. Pierwszym z <xref:System.Random> nich jest obiekt, jak ten, którego użyłeś w grze quizu matematycznego. Jest używany w tym kodzie, aby losowo wybierać komórki w TableLayoutPanel. Drugi obiekt, który może być dla <xref:System.Collections.Generic.List%601> Ciebie nowy, jest obiektem, który jest używany do przechowywania losowo wybranych symboli.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>Aby dodać losowy obiekt i listę ikon

1. W **Eksploratorze rozwiązań**wybierz *opcję Form1.cs,* jeśli używasz języka C#, lub *Form1.vb,* jeśli używasz języka Visual Basic, a następnie na pasku menu wybierz pozycję **Wyświetl** > **kod**. Alternatywnie można wybrać klawisz **F7** lub dwukrotnie kliknąć przycisk **Form1** w **Eksploratorze rozwiązań**.

     Spowoduje to wyświetlenie modułu kodu formularza Form1.

2. W istniejącym kodzie dodaj następujący kod.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

      > [!IMPORTANT]
      > Użyj formantu języka programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu języka C# lub fragment kodu języka Visual Basic.<br><br>![Sterowanie językiem programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

      Jeśli używasz języka C#, upewnij się, że kod jest umieszczany po otwarciu nawiasu klamrowego i tuż po deklaracji klasy (`public partial class Form1 : Form`). Jeśli używasz języka Visual Basic, umieść kod zaraz`Public Class Form1`po deklaracji klasy ( ).

3. Podczas dodawania list obiektu, należy zauważyć, **IntelliSense** okno, które otwiera. Poniżej znajduje się przykład języka C#, ale podobny tekst pojawia się po dodaniu listy w języku Visual Basic.

     ![Okno Właściwości pokazujące zdarzenie Kliknij](../ide/media/express_listintellisense.png)<br/>*Okno **IntelliSense***

    > [!NOTE]
    > Okno IntelliSense pojawia się tylko po ręcznym wprowadzeniu kodu. Nie pojawia się, jeśli kopiujesz i wklejasz kod.

     Jeśli spojrzysz na kod (i uwagi) w krótkich sekcjach, jest bardziej zrozumiały. Programy mogą używać obiektów listy do śledzenia wielu różnych typów elementów. Lista może zawierać liczby, wartości true/false, tekst lub inne obiekty. Można nawet mieć obiekt listy, który zawiera inne obiekty listy. Elementy na liście są nazywane elementami, a każda lista zawiera tylko jeden typ elementu. Tak więc, lista liczb może zawierać tylko liczby — nie można dodać tekstu do tej listy. Podobnie nie można dodać liczb do listy wartości true/false.

     Podczas tworzenia `List` obiektu przy `new` użyciu instrukcji, należy określić rodzaj danych, które mają być przechowywane w nim. Dlatego etykietka narzędzia w górnej części okna **IntelliSense** pokazuje typy elementów na liście. Ponadto, to, `List<string>` co (w języku `List(Of String)` C#) i (w języku `List` Visual Basic) `string` oznacza: Jest to obiekt, który zawiera elementy typu danych. Ciąg jest to, co program używa do przechowywania tekstu, który jest to, co etykietka narzędzia po prawej stronie okna **IntelliSense** mówi.

4. Należy wziąć pod uwagę, dlaczego w języku Visual Basic tablicy tymczasowej musi być utworzony najpierw, ale w języku C#, lista może być utworzona za pomocą jednej instrukcji. Jest to spowodowane języka C# ma *inicjatorów kolekcji*, które przygotowują listę do akceptowania wartości. W Visual Basic można używać inicjatora kolekcji. Jednak ze względu na zgodność z poprzednią wersją Visual Basic, zalecamy używanie poprzedniego kodu.

     Podczas korzystania z inicjatora `new` kolekcji z instrukcją, po utworzeniu nowego obiektu List program wypełnia go danymi podanymi wewnątrz nawiasów klamrowych. W takim przypadku otrzymasz listę ciągów o nazwie ikony i ta lista zostanie zainicjowana tak, że zawiera szesnaście ciągów. Każdy z tych ciągów jest pojedynczą literą, a odpowiadają one wszystkim ikonom, które będą w etykietach. Tak więc gra będzie miała parę wykrzykników, parę wielkich liter N, parę przecinków itd. (Gdy te znaki są ustawione na czcionkę Webdings, będą wyświetlane jako symbole, takie jak autobus, rower, pająk i tak dalej.) Obiekt listy będzie miał szesnaście ciągów, po jednym dla każdej komórki w panelu TableLayoutPanel.

    > [!NOTE]
    > W języku Visual Basic otrzymasz ten sam wynik, ale najpierw ciągi są umieszczane w tablicy tymczasowej, która jest następnie konwertowana na obiekt listy. Tablica jest podobna do listy, z tym wyjątkiem, że np. tablice są tworzone z ustalonym rozmiarem. Listy można zmniejszać i zwiększać stosownie do potrzeb, co jest istotne w tym programie.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [**Krok 3: Przypisywanie losowej ikony do każdej etykiety**](../ide/step-3-assign-a-random-icon-to-each-label.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 1: Tworzenie projektu i dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
