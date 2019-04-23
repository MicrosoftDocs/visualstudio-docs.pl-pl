---
title: Krok 2. Dodawanie obiektu losowego i listy ikon | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e71debec563aa54d5232686b599f286d147b1a7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073010"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Krok 2. Dodawanie obiektu losowego i listy ikon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym kroku utworzysz zestaw pasujących symboli dla gry. Każdy symbol jest dodawany do dwóch losowych komórek w TableLayoutPanel na formularzu. Aby to zrobić, użyj dwóch `new` instrukcji, aby utworzyć dwa obiekty. Pierwsza to `Random` obiektu, takiego jak używany w grze quiz matematyczny. Jest używany w tym kodzie, aby losowo wybierać komórki w TableLayoutPanel. Drugi obiekt, który może być dla Ciebie nowe, jest `List` obiektu, który jest używany do przechowywania losowo wybranych symboli.  
  
### <a name="to-add-a-random-object-and-a-list-of-icons"></a>Aby dodać obiekt losowy (Random) i listę ikon  
  
1. W **Eksploratora rozwiązań**, wybierz **Form1.cs** Jeśli używasz języka Visual C# lub **Form1.vb** Jeśli używasz Visual Basic, a następnie na pasku menu wybierz **widoku** , **Kodu**. Alternatywnie, możesz wybrać **F7** klucza, lub kliknij dwukrotnie **Form1** w **Eksploratora rozwiązań**.  
  
     Spowoduje to wyświetlenie modułu kodu formularza Form1.  
  
2. W istniejącym kodzie dodaj następujący kod.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#1)]  
  
     Jeśli używasz Visual C#, należy się, że umieszczasz kod po otwierającym nawiasie klamrowym i zaraz po deklaracji klasy (`public partial class Form1 : Form`). Jeśli używasz języka Visual Basic, umieść kod bezpośrednio po deklaracji klasy (`Public Class Form1`).  
  
3. Podczas dodawania `List` obiektów, zwróć uwagę, **IntelliSense** otwartym oknie. Poniżej przedstawiono przykład Visual C#, ale podobny tekst jest wyświetlany po dodaniu listy w Visual Basic.  
  
     ![Okno właściwości pokazujące kliknij zdarzenie](../ide/media/express-listintellisense.png "Express_ListIntellisense")  
Okno technologii IntelliSense  
  
    > [!NOTE]
    >  Okno Intellisense pojawia się tylko wtedy, gdy wprowadzasz kod ręcznie. Nie pojawia się, jeśli kopiujesz i wklejasz kod.  
  
     Jeśli spojrzysz na kod (i uwagi) w krótkich sekcjach, jest bardziej zrozumiały. Programy mogą korzystać `List` obiekty do śledzenia wielu różnych typów elementów. Lista może zawierać liczby, wartości true/false, tekst lub inne obiekty. Można nawet mieć `List` obiekt, który przechowuje inne `List` obiektów. Elementy na liście są nazywane *elementy*, a każda lista zawiera tylko jeden typ elementu. Tak więc, lista liczb może zawierać tylko liczby — nie można dodać tekstu do tej listy. Podobnie nie można dodać liczb do listy wartości true/false.  
  
     Po utworzeniu `List` przy użyciu `new` instrukcji, należy określić rodzaj danych, które mają być przechowywane w nim. Dlatego dymek u góry **IntelliSense** okno zawiera typy elementów na liście. Ponadto, właśnie to `List<string>` (w elemencie wizualnym C#) i `List(Of String)` (w języku Visual Basic) oznacza, że: Jest `List` obiekt, który przechowuje elementy `string` typu danych. Ciąg to, czego program używa do przechowywania tekstu, który ma co wyświetla dymek z prawej strony **IntelliSense** okno to coś.  
  
4. Zastanów się, dlaczego w Visual Basic należy najpierw utworzyć tablicę tymczasową, a w Visual C# lista może być utworzona za pomocą jednej instrukcji. Jest to spowodowane języka Visual C# ma *inicjatory kolekcji*, które przygotowują listę do przyjmowania wartości. W Visual Basic można używać inicjatora kolekcji. Jednak ze względu na zgodność z poprzednią wersją Visual Basic, zalecamy używanie poprzedniego kodu.  
  
     Kiedy używasz inicjatora kolekcji z `new` instrukcji po nowym `List` obiekt zostanie utworzony, program wypełnia go danymi dostarczonymi wewnątrz nawiasów klamrowych. W takim przypadku otrzymujesz listę ciągów o nazwie **ikony**, oraz że lista zostanie zainicjowana tak, aby zawierała szesnaście ciągów. Każdy z tych ciągów jest pojedynczą literą, a odpowiadają one wszystkim ikonom, które będą w etykietach. Tak więc gra będzie miała parę wykrzykników, parę wielkich liter N, parę przecinków itd. (Kiedy te znaki są ustawione na czcionkę Webdings, będą one występować jako symbole, takie jak autobus, rower, pająk i tak dalej). Twoje `List` obiekt będzie miał razem szesnaście ciągów we wszystkich, jeden dla każdej komórki w panelu TableLayoutPanel.  
  
    > [!NOTE]
    >  W języku Visual Basic, uzyskujesz ten sam wynik, ale najpierw ciągi są wprowadzane do tablicy tymczasowej, która jest następnie przekształcana w `List` obiektu. Tablica jest podobna do listy, z tym wyjątkiem, że np. tablice są tworzone z ustalonym rozmiarem. Listy można zmniejszać i zwiększać stosownie do potrzeb, co jest istotne w tym programie.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Aby przejść do następnego kroku samouczka, zobacz [krok 3: Przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md).  
  
- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1: Tworzenie projektu i Dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
