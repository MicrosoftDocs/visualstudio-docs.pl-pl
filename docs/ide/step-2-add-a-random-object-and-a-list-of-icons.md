---
title: Krok 2. Dodawanie losowego obiektu i listy ikon
description: Dowiedz się, jak utworzyć zestaw pasujących symboli dla gry.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1018b390f6ebbf67fab88554aa85fe6a8ecec88d
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480697"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Krok 2. Dodawanie losowego obiektu i listy ikon

W tym kroku utworzysz zestaw pasujących symboli dla gry. Każdy symbol jest dodawany do dwóch losowych komórek w TableLayoutPanel na formularzu. W tym celu należy użyć dwóch `new` instrukcji, aby utworzyć dwa obiekty. Pierwszy to <xref:System.Random> obiekt, taki jak użyty w grze quizu matematycznego. Jest używany w tym kodzie, aby losowo wybierać komórki w TableLayoutPanel. Drugi obiekt, który może być nowy dla Ciebie, jest <xref:System.Collections.Generic.List%601> obiektem, który jest używany do przechowywania losowo wybranych symboli.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>Aby dodać losowy obiekt i listę ikon

1. W **Eksplorator rozwiązań** wybierz opcję *Form1.cs* , jeśli używasz języka C# lub *Form1. vb* , jeśli używasz Visual Basic, a następnie na pasku menu wybierz polecenie **Wyświetl**  >  **kod**. Alternatywnie można wybrać klawisz **F7** lub kliknąć dwukrotnie przycisk **Form1** w **Eksplorator rozwiązań**.

     Spowoduje to wyświetlenie modułu kodu formularza Form1.

2. W istniejącym kodzie dodaj następujący kod.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

      > [!IMPORTANT]
      > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu w języku C# lub fragment kodu Visual Basic.<br><br>![Kontrolka języka programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

      Jeśli używasz języka C#, upewnij się, że kod został umieszczony po otwierającym nawiasie klamrowym i zaraz po deklaracji klasy ( `public partial class Form1 : Form` ). Jeśli używasz Visual Basic, umieść kod bezpośrednio po deklaracji klasy ( `Public Class Form1` ).

3. Podczas dodawania obiektu list należy zauważyć, że zostanie otwarte okno **IntelliSense** . Poniżej znajduje się przykładowy kod w języku C#, ale podobny tekst pojawia się po dodaniu listy w Visual Basic.

     ![Okno Właściwości pokazujące zdarzenie Kliknij](../ide/media/express_listintellisense.png)<br/>*Okno *_IntelliSense_**

    > [!NOTE]
    > Okno IntelliSense pojawia się tylko wtedy, gdy ręcznie wprowadzasz kod. Nie pojawia się, jeśli kopiujesz i wklejasz kod.

     Jeśli spojrzysz na kod (i uwagi) w krótkich sekcjach, jest bardziej zrozumiały. Programy mogą używać obiektów list, aby śledzić wiele różnych typów elementów. Lista może zawierać liczby, wartości true/false, tekst lub inne obiekty. Można nawet mieć obiekt listy, który zawiera inne obiekty list. Elementy na liście są nazywane elementami, a każda lista zawiera tylko jeden typ elementu. Tak więc, lista liczb może zawierać tylko liczby — nie można dodać tekstu do tej listy. Podobnie nie można dodać liczb do listy wartości true/false.

     Podczas tworzenia `List` obiektu przy użyciu instrukcji należy `new` określić rodzaj danych, które mają być w niej przechowywane. Dlatego etykietka narzędzia w górnej części okna **IntelliSense** pokazuje typy elementów na liście. Ponadto jest to `List<string>` element (w języku C#) i `List(Of String)` (w Visual Basic): jest to `List` obiekt, który przechowuje elementy `string` typu danych. Ciąg jest używany przez program do przechowywania tekstu, co oznacza, że po prawej stronie okna **IntelliSense** jest wyświetlana etykietka narzędzia.

4. Rozważmy, dlaczego w Visual Basic należy najpierw utworzyć tablicę tymczasową, ale w języku C# można utworzyć listę z jedną instrukcją. Wynika to z faktu, że język C# ma *Inicjatory kolekcji*, przygotowując listę do akceptowania wartości. W Visual Basic można używać inicjatora kolekcji. Jednak ze względu na zgodność z poprzednią wersją Visual Basic, zalecamy używanie poprzedniego kodu.

     Gdy używasz inicjatora kolekcji z `new` instrukcją, po utworzeniu nowego obiektu listy program wypełnia go danymi dostarczonymi wewnątrz nawiasów klamrowych. W tym przypadku otrzymujesz listę ciągów o nazwanych ikonach, a ta lista zostanie zainicjowana tak, aby zawierała szesnaste ciągi. Każdy z tych ciągów jest pojedynczą literą, a odpowiadają one wszystkim ikonom, które będą w etykietach. Tak więc gra będzie miała parę wykrzykników, parę wielkich liter N, parę przecinków itd. (Gdy te znaki są ustawione na czcionkę Webdings, będą wyświetlane jako symbole, takie jak magistrala, rower, Pająk itd.) Obiekt listy będzie zawierać szesnaste ciągi, po jednym dla każdej komórki w panelu TableLayoutPanel.

    > [!NOTE]
    > W Visual Basic otrzymujesz ten sam wynik, ale najpierw ciągi są umieszczane w tablicy tymczasowej, która jest następnie konwertowana do obiektu listy. Tablica jest podobna do listy, z tym wyjątkiem, że np. tablice są tworzone z ustalonym rozmiarem. Listy można zmniejszać i zwiększać stosownie do potrzeb, co jest istotne w tym programie.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [**krok 3. przypisanie losowej ikony do każdej etykiety**](../ide/step-3-assign-a-random-icon-to-each-label.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1. Tworzenie projektu i Dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
