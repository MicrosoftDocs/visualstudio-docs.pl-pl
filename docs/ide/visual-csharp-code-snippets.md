---
title: Fragmenty kodu w języku C#
description: Dowiedz się, jak za pomocą fragmentów kodu dodać powszechnie używany kod do plików kodu w języku C#.
ms.custom: SEO-VS-2020
ms.date: 06/05/2017
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e4656e0769075be26db5bd06108093a49fb5e2af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941544"
---
# <a name="c-code-snippets"></a>Fragmenty kodu w języku C#

Fragmenty kodu są gotowymi fragmentami kodu, które można szybko wstawić do kodu. Na przykład `for` fragment kodu tworzy pustą `for` pętlę. Niektóre fragmenty kodu są otoczone fragmentami kodu, które umożliwiają wybranie wierszy kodu, a następnie wybranie fragmentu kodu, który zawiera zaznaczone wiersze kodu. Na przykład po wybraniu wierszy kodu, a następnie aktywowaniu `for` fragmentu kodu, tworzy `for` pętlę z tymi wierszami kodu w bloku pętli. Fragmenty kodu mogą szybciej i bardziej niezawodnie pisać kod programu.

Można wstawić fragment kodu w lokalizacji kursora lub wstawić fragment kodu otaczającego wokół aktualnie zaznaczonego kodu. Wstawianie fragmentu kodu jest wywoływane przez **Wstawianie fragmentu kodu** lub **Otocz za** pomocą poleceń w menu **IntelliSense** lub za pomocą skrótów klawiaturowych **Ctrl** + **k**,**X** lub **Ctrl** + **k**, odpowiednio.

Wstawienie wstawka **kodu** zawiera nazwę fragmentu kodu dla wszystkich dostępnych fragmentów kodu. Wstawianie fragmentów kodu zawiera również okno dialogowe dane wejściowe, w którym można wpisać nazwę fragmentu kodu lub część nazwy fragmentu kodu. Wstawianie fragmentu kodu wyróżnia najbliższe dopasowanie do nazwy fragmentu kodu. Naciśnięcie klawisza **Tab** w dowolnym momencie spowoduje odrzucenie wstawionego fragmentu kodu i wstawienie aktualnie zaznaczonego fragmentu kodu. Naciśnięcie klawisza **ESC** lub kliknięcie myszy w edytorze kodu spowoduje odrzucenie wstawionego fragmentu kodu bez wstawiania fragmentu kodu.

## <a name="default-code-snippets"></a>Domyślne fragmenty kodu

Domyślnie następujące fragmenty kodu są zawarte w programie Visual Studio dla języka C#.

|Nazwa (lub skrót)|Opis|Prawidłowe lokalizacje do wstawienia fragmentu kodu|
| - |-----------------| - |
|#if|Tworzy dyrektywę [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) i [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) dyrektywą.|Dowolnym miejscu.|
|#region|Tworzy dyrektywę [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) i [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) dyrektywą.|Dowolnym miejscu.|
|~|Tworzy [finalizator](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (destruktor) dla klasy zawierającej.|Wewnątrz klasy.|
|— atrybut|Tworzy deklarację dla klasy, która pochodzi od <xref:System.Attribute> .|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|checked|Tworzy [zaznaczony](/dotnet/csharp/language-reference/keywords/checked) blok.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|class|Tworzy deklarację klasy.|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|obiektów|Tworzy Konstruktor dla klasy zawierającej.|Wewnątrz klasy.|
|CW|Tworzy wywołanie <xref:System.Console.WriteLine%2A> .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|do|Tworzy [](/dotnet/csharp/language-reference/keywords/do) `while` pętlę do.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|else|Tworzy blok [else](/dotnet/csharp/language-reference/keywords/if-else) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|enum|Tworzy deklarację [wyliczenia](/dotnet/csharp/language-reference/keywords/enum) .|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|equals|Tworzy deklarację metody, która zastępuje <xref:System.Object.Equals%2A> metodę zdefiniowaną w <xref:System.Object> klasie.|Wewnątrz klasy lub struktury.|
|Oprócz|Tworzy deklarację dla klasy, która pochodzi od wyjątku (domyślnie <xref:System.Exception> ).|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|dla|Tworzy pętlę [for](/dotnet/csharp/language-reference/keywords/for) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|foreach|Tworzy pętlę [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|dla|Tworzy pętlę [for](/dotnet/csharp/language-reference/keywords/for) , która zmniejsza zmienną pętli po każdej iteracji.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|if|Tworzy blok [if](/dotnet/csharp/language-reference/keywords/if-else) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|indeksatora|Tworzy deklarację indeksatora.|Wewnątrz klasy lub struktury.|
|interface|Tworzy deklarację [interfejsu](/dotnet/csharp/language-reference/keywords/interface) .|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|wywołuje|Tworzy blok, który bezpiecznie wywołuje zdarzenie.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|iterator|Tworzy iterator.|Wewnątrz klasy lub struktury.|
|iterindex|Tworzy parę iteratorów i indeksatora "Named" przy użyciu klasy zagnieżdżonej.|Wewnątrz klasy lub struktury.|
|lock|Tworzy blok [blokady](/dotnet/csharp/language-reference/keywords/lock-statement) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|mbox|Tworzy wywołanie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> . Może być konieczne dodanie odwołania do *System.Windows.Forms.dll*.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|namespace|Tworzy deklarację [przestrzeni nazw](/dotnet/csharp/language-reference/keywords/namespace) .|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw).|
|wierszy|Tworzy [automatycznie implementowaną](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) deklarację właściwości.|Wewnątrz klasy lub struktury.|
|propfull|Tworzy deklarację właściwości z metodyą `get` `set` dostępu i.|Wewnątrz klasy lub struktury.|
|propg|Tworzy [automatycznie zaimplementowaną Właściwość](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) tylko do odczytu z prywatnym `set` akcesorem.|Wewnątrz klasy lub struktury.|
|kartę|Tworzy [statyczną](/dotnet/csharp/language-reference/keywords/static) deklarację metody [całkowitej int](/dotnet/csharp/language-reference/keywords/int) .|Wewnątrz klasy lub struktury.|
|struktura|Tworzy deklarację [struktury](/dotnet/csharp/language-reference/keywords/struct) .|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|svm|Tworzy [statyczną](/dotnet/csharp/language-reference/keywords/static) deklarację metody " [void](/dotnet/csharp/language-reference/keywords/void) Main".|Wewnątrz klasy lub struktury.|
|switch|Tworzy blok [przełącznika](/dotnet/csharp/language-reference/keywords/switch) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|try|Tworzy blok [try-catch](/dotnet/csharp/language-reference/keywords/try-catch) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|tryf|Tworzy blok [try-finally](/dotnet/csharp/language-reference/keywords/try-finally) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|unchecked|Tworzy [niesprawdzony](/dotnet/csharp/language-reference/keywords/unchecked) blok.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|unsafe|Tworzy [niebezpieczny](/dotnet/csharp/language-reference/keywords/unsafe) blok.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|using|Tworzy dyrektywę [using](/dotnet/csharp/language-reference/keywords/using-directive) .|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw).|
|while|Tworzy pętlę [while](/dotnet/csharp/language-reference/keywords/while) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|

## <a name="see-also"></a>Zobacz też

- [Funkcje fragmentów kodu](../ide/code-snippet-functions.md)
- [Fragmenty kodu](../ide/code-snippets.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Instrukcje: używanie fragmentów kodu w cudzysłowie](../ide/how-to-use-surround-with-code-snippets.md)
