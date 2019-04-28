---
title: Krok 2. Dodawanie obiektu Random i listy ikon
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23117079dd0cd593446ce8af277670a643c820b3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430808"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Krok 2. Dodawanie obiektu Random i listy ikon
W tym kroku utworzysz zestaw pasujących symboli dla gry. Każdy symbol jest dodawany do dwóch losowych komórek w TableLayoutPanel na formularzu. Aby to zrobić, użyj dwóch `new` instrukcji, aby utworzyć dwa obiekty. Pierwsza to <xref:System.Random> obiektu, takiego jak używany w grze quiz matematyczny. Jest używany w tym kodzie, aby losowo wybierać komórki w TableLayoutPanel. Drugi obiekt, który może być dla Ciebie nowe, jest <xref:System.Collections.Generic.List%601> obiektu, który jest używany do przechowywania losowo wybranych symboli.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>Aby dodać obiektu losowego i listy ikon

1. W **Eksploratora rozwiązań**, wybierz *Form1.cs* Jeśli używasz Visual C#, lub *Form1.vb* Jeśli używasz Visual Basic, a następnie na pasku menu wybierz **Widoku** > **kodu**. Alternatywnie, możesz wybrać **F7** klucza, lub kliknij dwukrotnie **Form1** w **Eksploratora rozwiązań**.

     Spowoduje to wyświetlenie modułu kodu formularza Form1.

2. W istniejącym kodzie dodaj następujący kod.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

     Jeśli używasz Visual C#, należy się, że umieszczasz kod po otwierającym nawiasie klamrowym i zaraz po deklaracji klasy (`public partial class Form1 : Form`). Jeśli używasz języka Visual Basic, umieść kod bezpośrednio po deklaracji klasy (`Public Class Form1`).

3. Zwróć uwagę, dodając obiekt listy, **IntelliSense** otwartym oknie. Poniżej przedstawiono przykład Visual C#, ale podobny tekst jest wyświetlany po dodaniu listy w Visual Basic.

     ![Okno właściwości pokazujące kliknij zdarzenie](../ide/media/express_listintellisense.png) okno technologii IntelliSense

    > [!NOTE]
    > Okno IntelliSense pojawia się tylko wtedy, gdy wprowadzasz kod ręcznie. Nie pojawia się, jeśli kopiujesz i wklejasz kod.

     Jeśli spojrzysz na kod (i uwagi) w krótkich sekcjach, jest bardziej zrozumiały. Programy mogą korzystać z listy obiektów, aby śledzić wiele różnych typów elementów. Lista może zawierać liczby, wartości true/false, tekst lub inne obiekty. Można nawet mieć obiekt listy, który przechowuje inne obiekty listy. Elementy na liście są nazywane elementami, a każda lista zawiera tylko jeden typ elementu. Tak więc, lista liczb może zawierać tylko liczby — nie można dodać tekstu do tej listy. Podobnie nie można dodać liczb do listy wartości true/false.

     Po utworzeniu `List` przy użyciu `new` instrukcji, należy określić rodzaj danych, które mają być przechowywane w nim. Dlatego dymek u góry **IntelliSense** okno zawiera typy elementów na liście. Ponadto, właśnie to `List<string>` (w elemencie wizualnym C#) i `List(Of String)` (w języku Visual Basic) oznacza, że: Jest `List` obiekt, który przechowuje elementy `string` typu danych. Ciąg to, czego program używa do przechowywania tekstu, który ma co wyświetla dymek z prawej strony **IntelliSense** okno to coś.

4. Zastanów się, dlaczego w Visual Basic należy najpierw utworzyć tablicę tymczasową, a w Visual C# lista może być utworzona za pomocą jednej instrukcji. Jest to spowodowane języka Visual C# ma *inicjatory kolekcji*, które przygotowują listę do przyjmowania wartości. W Visual Basic można używać inicjatora kolekcji. Jednak ze względu na zgodność z poprzednią wersją Visual Basic, zalecamy używanie poprzedniego kodu.

     Kiedy używasz inicjatora kolekcji z `new` instrukcji, po utworzeniu nowego obiektu listy program wypełnia go danymi dostarczonymi wewnątrz nawiasów klamrowych. W takim przypadku otrzymujesz listę ciągów o nazwie ikon, a ta lista zostanie zainicjowana tak, aby zawierała szesnaście ciągów. Każdy z tych ciągów jest pojedynczą literą, a odpowiadają one wszystkim ikonom, które będą w etykietach. Tak więc gra będzie miała parę wykrzykników, parę wielkich liter N, parę przecinków itd. (Kiedy te znaki są ustawione na czcionkę Webdings, będą one występować jako symbole, takie jak autobus, rower, pająk i tak dalej). Obiekt listy będzie miał razem szesnaście ciągów we wszystkich, jeden dla każdej komórki w panelu TableLayoutPanel.

    > [!NOTE]
    > W języku Visual Basic uzyskujesz ten sam wynik, ale najpierw ciągi są wprowadzane do tablicy tymczasowej, która jest następnie przekształcana w obiekt listy. Tablica jest podobna do listy, z tym wyjątkiem, że np. tablice są tworzone z ustalonym rozmiarem. Listy można zmniejszać i zwiększać stosownie do potrzeb, co jest istotne w tym programie.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 3: Przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1: Tworzenie projektu i Dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
