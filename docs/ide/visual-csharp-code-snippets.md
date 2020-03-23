---
title: Fragmenty kodu języka C#
ms.date: 06/05/2017
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d41907a15b7e0b1692dda3f4d678c2b843dfcd03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594165"
---
# <a name="c-code-snippets"></a>Fragmenty kodu języka C#

Fragmenty kodu są gotowe fragmenty kodu można szybko wstawić do kodu. Na przykład `for` fragment kodu tworzy pustą `for` pętlę. Niektóre fragmenty kodu są otoczki kodu, które umożliwiają wybranie wierszy kodu, a następnie wybierz fragment kodu, który zawiera wybrane wiersze kodu. Na przykład po wybraniu wierszy kodu, a następnie aktywować fragment `for` kodu, tworzy pętlę `for` z tych wierszy kodu wewnątrz bloku pętli. Fragmenty kodu mogą przyspieszyć, ułatwić i bardziej niezawodne pisanie kodu programu.

Można wstawić fragment kodu w lokalizacji kursora lub wstawić fragment kodu surround z fragmentem kodu wokół aktualnie wybranego kodu. Wstawiacz fragmentów kodu jest wywoływany za pomocą poleceń **Wstaw kod** lub **Surround With** w menu **IntelliSense** lub za pomocą skrótów klawiaturowych **Ctrl**+**K,****X** lub **Ctrl**+**K**,**S.**

**W inserter urywek kodu** wyświetla nazwę fragmentu kodu dla wszystkich dostępnych fragmentów kodu. Inserter urywek kodu zawiera również okno dialogowe wprowadzania, w którym można wpisać nazwę fragmentu kodu lub część nazwy fragmentu kodu. Wbudowany fragment kodu podświetla najbliższe dopasowanie do nazwy fragmentu kodu. Naciśnięcie **klawisza Tab** w dowolnym momencie spowoduje odrzucenie insertera fragmentu kodu i wstawienie aktualnie wybranego fragmentu kodu. Naciśnięcie **klawisza Esc** lub kliknięcie myszą w edytorze kodu spowoduje odrzucenie insertera fragmentu kodu bez wstawiania fragmentu kodu.

## <a name="default-code-snippets"></a>Domyślne fragmenty kodu

Domyślnie następujące fragmenty kodu są zawarte w programie Visual Studio dla języka C#.

|Nazwa (lub skrót)|Opis|Prawidłowe lokalizacje do wstawiania fragmentu kodu|
| - |-----------------| - |
|#if|Tworzy [dyrektywę #if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) i [dyrektywę #endif.](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif)|Dowolnym miejscu.|
|#region|Tworzy [dyrektywę #region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) i [dyrektywę #endregion.](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion)|Dowolnym miejscu.|
|~|Tworzy [finalizator](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (destruktor) dla klasy zawierającej.|Wewnątrz klasy.|
| — atrybut|Tworzy deklarację dla klasy, <xref:System.Attribute>która wywodzi się z .|Wewnątrz obszaru nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|checked|Tworzy [zaznaczony](/dotnet/csharp/language-reference/keywords/checked) blok.|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|class|Tworzy deklarację klasy.|Wewnątrz obszaru nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|Konstruktor|Tworzy konstruktora dla klasy zawierającej.|Wewnątrz klasy.|
|Cw|Tworzy wywołanie <xref:System.Console.WriteLine%2A>do .|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|do|Tworzy pętlę [do.](/dotnet/csharp/language-reference/keywords/do) `while`|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|else|Tworzy [blok inny.](/dotnet/csharp/language-reference/keywords/if-else)|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|enum|Tworzy deklarację [wyliczenia.](/dotnet/csharp/language-reference/keywords/enum)|Wewnątrz obszaru nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|equals|Tworzy deklarację metody, która <xref:System.Object.Equals%2A> zastępuje metodę <xref:System.Object> zdefiniowaną w klasie.|Wewnątrz klasy lub struktury.|
|Wyjątek|Tworzy deklarację dla klasy, która pochodzi<xref:System.Exception> od wyjątku (domyślnie).|Wewnątrz obszaru nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|for|Tworzy [pętlę for.](/dotnet/csharp/language-reference/keywords/for)|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|foreach|Tworzy pętlę [foreach.](/dotnet/csharp/language-reference/keywords/foreach-in)|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|forr (forr)|Tworzy [for](/dotnet/csharp/language-reference/keywords/for) pętli, która zmniejsza zmiennej pętli po każdej iteracji.|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|if|Tworzy blok [if.](/dotnet/csharp/language-reference/keywords/if-else)|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|Indeksatora|Tworzy deklarację indeksatora.|Wewnątrz klasy lub struktury.|
|interface|Tworzy deklarację [interfejsu.](/dotnet/csharp/language-reference/keywords/interface)|Wewnątrz obszaru nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|Wywołać|Tworzy blok, który bezpiecznie wywołuje zdarzenie.|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|iterator|Tworzy iterator.|Wewnątrz klasy lub struktury.|
|iterindex|Tworzy "nazwany" pary iteratora i indeksatora przy użyciu klasy zagnieżdżonej.|Wewnątrz klasy lub struktury.|
|lock|Tworzy blok [blokady.](/dotnet/csharp/language-reference/keywords/lock-statement)|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|Mbox|Tworzy wywołanie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>do . Może być trzeba dodać odwołanie do *pliku System.Windows.Forms.dll*.|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|przestrzeń nazw|Tworzy deklarację [obszaru nazw.](/dotnet/csharp/language-reference/keywords/namespace)|Wewnątrz obszaru nazw (w tym globalnej przestrzeni nazw).|
|Wniosku|Tworzy [automatycznie zaimplementowane](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) deklaracji właściwości.|Wewnątrz klasy lub struktury.|
|propfull|Tworzy deklarację `get` właściwości `set` z i akcesorów.|Wewnątrz klasy lub struktury.|
|propg (propg)|Tworzy właściwości tylko do odczytu [autoimplementowane](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) z prywatnego `set` akcesora.|Wewnątrz klasy lub struktury.|
|Sim|Tworzy [statyczną](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) Main deklaracji metody.|Wewnątrz klasy lub struktury.|
|struktura |Tworzy deklarację [struktury.](/dotnet/csharp/language-reference/keywords/struct)|Wewnątrz obszaru nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|Svm|Tworzy [statyczną](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void) Main deklaracji metody.|Wewnątrz klasy lub struktury.|
|switch|Tworzy blok [przełącznika.](/dotnet/csharp/language-reference/keywords/switch)|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|try|Tworzy blok [try-catch.](/dotnet/csharp/language-reference/keywords/try-catch)|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|tryf ( tryf )|Tworzy blok [try-finally.](/dotnet/csharp/language-reference/keywords/try-finally)|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|unchecked|Tworzy [niezaznaczony](/dotnet/csharp/language-reference/keywords/unchecked) blok.|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|unsafe|Tworzy [niebezpieczny](/dotnet/csharp/language-reference/keywords/unsafe) blok.|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|
|using|Tworzy [using](/dotnet/csharp/language-reference/keywords/using-directive) dyrektywy.|Wewnątrz obszaru nazw (w tym globalnej przestrzeni nazw).|
|while|Tworzy pętlę [while.](/dotnet/csharp/language-reference/keywords/while)|Wewnątrz metody indeksatora, akcesor właściwości lub akcesor zdarzeń.|

## <a name="see-also"></a>Zobacz też

- [Funkcje fragmentów kodu](../ide/code-snippet-functions.md)
- [Fragmenty kodu](../ide/code-snippets.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Jak: Używanie fragmentów kodu surround-with](../ide/how-to-use-surround-with-code-snippets.md)
