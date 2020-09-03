---
title: Krok 2. Dodawanie losowego obiektu i listy ikon | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7370bf956fd79f5568737af5d9a96b9c64a5316b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667314"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Krok 2. Dodawanie obiektu losowego i listy ikon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym kroku utworzysz zestaw pasujących symboli dla gry. Każdy symbol jest dodawany do dwóch losowych komórek w TableLayoutPanel na formularzu. W tym celu należy użyć dwóch `new` instrukcji, aby utworzyć dwa obiekty. Pierwszy to `Random` obiekt, taki jak użyty w grze quizu matematycznego. Jest używany w tym kodzie, aby losowo wybierać komórki w TableLayoutPanel. Drugi obiekt, który może być nowy dla Ciebie, jest `List` obiektem, który jest używany do przechowywania losowo wybranych symboli.

### <a name="to-add-a-random-object-and-a-list-of-icons"></a>Aby dodać obiekt losowy (Random) i listę ikon

1. W **Eksplorator rozwiązań**wybierz opcję **Form1.cs** , jeśli używasz języka Visual C# lub **Form1. vb** , jeśli używasz Visual Basic, a następnie na pasku menu wybierz **Widok**, **kod**. Alternatywnie można wybrać klawisz **F7** lub kliknąć dwukrotnie przycisk **Form1** w **Eksplorator rozwiązań**.

     Spowoduje to wyświetlenie modułu kodu formularza Form1.

2. W istniejącym kodzie dodaj następujący kod.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#1)]

     Jeśli używasz języka Visual C#, upewnij się, że kod został umieszczony po otwierającym nawiasie klamrowym i zaraz po deklaracji klasy ( `public partial class Form1 : Form` ). Jeśli używasz Visual Basic, umieść kod bezpośrednio po deklaracji klasy ( `Public Class Form1` ).

3. Podczas dodawania `List` obiektu Zwróć uwagę na okno **IntelliSense** , które jest otwierane. Poniżej przedstawiono przykład Visual C#, ale podobny tekst jest wyświetlany po dodaniu listy w Visual Basic.

     ![Okno właściwości pokazać zdarzenia kliknięcia](../ide/media/express-listintellisense.png "Express_ListIntellisense") Okno IntelliSense

    > [!NOTE]
    > Okno Intellisense pojawia się tylko wtedy, gdy wprowadzasz kod ręcznie. Nie pojawia się, jeśli kopiujesz i wklejasz kod.

     Jeśli spojrzysz na kod (i uwagi) w krótkich sekcjach, jest bardziej zrozumiały. Programy mogą używać `List` obiektów do śledzenia wielu różnych typów elementów. Lista może zawierać liczby, wartości true/false, tekst lub inne obiekty. Można nawet mieć `List` obiekt, który zawiera inne `List` obiekty. Elementy na liście są nazywane *elementami*, a każda lista zawiera tylko jeden typ elementu. Tak więc, lista liczb może zawierać tylko liczby — nie można dodać tekstu do tej listy. Podobnie nie można dodać liczb do listy wartości true/false.

     Podczas tworzenia `List` obiektu przy użyciu instrukcji należy `new` określić rodzaj danych, które mają być w niej przechowywane. Dlatego etykietka narzędzia w górnej części okna **IntelliSense** pokazuje typy elementów na liście. Ponadto jest to element `List<string>` (w języku Visual C#) i `List(Of String)` (w Visual Basic): jest to `List` obiekt, który przechowuje elementy `string` typu danych. Ciąg jest używany przez program do przechowywania tekstu, co oznacza, że po prawej stronie okna **IntelliSense** jest wyświetlana etykietka narzędzia.

4. Zastanów się, dlaczego w Visual Basic należy najpierw utworzyć tablicę tymczasową, a w Visual C# lista może być utworzona za pomocą jednej instrukcji. Wynika to z faktu, że język Visual C# ma *Inicjatory kolekcji*, przygotowując listę do akceptowania wartości. W Visual Basic można używać inicjatora kolekcji. Jednak ze względu na zgodność z poprzednią wersją Visual Basic, zalecamy używanie poprzedniego kodu.

     Gdy używasz inicjatora kolekcji z `new` instrukcją, po `List` utworzeniu nowego obiektu program wypełnia go danymi dostarczonymi wewnątrz nawiasów klamrowych. W tym przypadku otrzymujesz listę ciągów o nazwanych **ikonach**, a ta lista zostanie zainicjowana tak, aby zawierała szesnaste ciągi. Każdy z tych ciągów jest pojedynczą literą, a odpowiadają one wszystkim ikonom, które będą w etykietach. Tak więc gra będzie miała parę wykrzykników, parę wielkich liter N, parę przecinków itd. (Gdy te znaki są ustawione na czcionkę Webdings, będą wyświetlane jako symbole, takie jak magistrala, rower, Pająk itd.) `List` Obiekt będzie zawierać szesnaste ciągi, po jednym dla każdej komórki w panelu TableLayoutPanel.

    > [!NOTE]
    > W Visual Basic otrzymujesz ten sam wynik, ale najpierw ciągi są umieszczane w tablicy tymczasowej, która jest następnie konwertowana na `List` obiekt. Tablica jest podobna do listy, z tym wyjątkiem, że np. tablice są tworzone z ustalonym rozmiarem. Listy można zmniejszać i zwiększać stosownie do potrzeb, co jest istotne w tym programie.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 3. przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1. Tworzenie projektu i Dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
