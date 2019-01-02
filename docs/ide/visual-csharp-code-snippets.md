---
title: C#fragmenty kodu
ms.date: 06/05/2017
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: be3af132a84b37043cf185beb26293ef5618439b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858246"
---
# <a name="c-code-snippets"></a>C#fragmenty kodu

Fragmenty kodu są gotowe fragmenty kodu, które szybko można wstawić w kodzie. Na przykład `for` fragment kodu tworzy pustą `for` pętli. Niektóre fragmenty kodu pochodzą z funkcji Otocz przez fragmenty kodu, które umożliwia wybór wierszy kodu, a następnie wybierz fragment kodu, która obejmuje też dokument wybranych wierszy kodu. Na przykład kiedy wybierz linii kodu i przy następnie uaktywnić `for` fragment kodu tworzy `for` pętli za pomocą tych wierszy kodu wewnątrz bloku pętli. Fragmenty kodu ułatwia pisanie program code szybsze, prostsze i bardziej niezawodne.

 Wstaw fragment kodu w lokalizacji kursora lub Wstaw Otocz przez fragment kodu wokół zaznaczonego kodu. Wstawianie wstawek kodu jest wywoływana za pomocą **Wstaw fragment kodu** lub **Otocz** polecenia na **IntelliSense** menu lub za pomocą skrótów klawiaturowych  **CTRL**+**K**,**X** lub **Ctrl**+**K**,**S** odpowiednio.

 **Wstawek kodu** Wyświetla nazwę fragment kodu dla wszystkich fragmentów kodu dostępne. Wstawianie wstawek kodu obejmuje również okno dialogowe danych wejściowych, w którym możesz wpisać nazwę fragmentu kodu lub część nazwy fragmentu kodu. Wstawianie wstawek kodu wyróżnia najlepiej dopasowany do nazwy fragmentu kodu. Naciśnięcie klawisza **kartę** w dowolnej chwili będzie odrzucić wstawek kodu i Wstaw fragment kodu aktualnie wybrany. Naciśnięcie klawisza **Esc** lub klikając przycisk myszy w edytorze kodu będą odrzucać wstawek kodu bez wstawiania fragmentu kodu.

## <a name="default-code-snippets"></a>Fragmenty kodu domyślnego

Domyślnie następujące fragmenty kodu są uwzględnione w programie Visual Studio dla C#.

|Nazwa (lub skrót)|Opis|Prawidłowe lokalizacje, aby wstawić fragment kodu|
| - |-----------------| - |
|#if|Tworzy [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) dyrektywy i [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) dyrektywy.|W dowolnym miejscu.|
|#region|Tworzy [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) dyrektywy i [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) dyrektywy.|W dowolnym miejscu.|
|~|Tworzy [finalizator](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (destruktor) zawierający klasy.|Wewnątrz klasy.|
|— atrybut|Tworzy oświadczenie dla klasy, która pochodzi od klasy <xref:System.Attribute>.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|checked|Tworzy [zaznaczone](/dotnet/csharp/language-reference/keywords/checked) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|class|Tworzy deklaracji klasy.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|ctor|Tworzy konstruktora dla klasy zawierającej.|Wewnątrz klasy.|
|cw|Tworzy wywołanie <xref:System.Console.WriteLine%2A>.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|do|Tworzy [czy](/dotnet/csharp/language-reference/keywords/do) `while` pętli.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|else|Tworzy [else](/dotnet/csharp/language-reference/keywords/if-else) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|enum|Tworzy [wyliczenia](/dotnet/csharp/language-reference/keywords/enum) deklaracji.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|equals|Tworzy deklaracji metody, która zastępuje <xref:System.Object.Equals%2A> metody zdefiniowanej w <xref:System.Object> klasy.|Wewnątrz klasy lub struktury.|
|wyjątek|Tworzy oświadczenie dla klasy, która wynika z wyjątku (<xref:System.Exception> domyślnie).|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|dla|Tworzy [dla](/dotnet/csharp/language-reference/keywords/for) pętli.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|foreach|Tworzy [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) pętli.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|lepiej wykorzystać możliwości|Tworzy [dla](/dotnet/csharp/language-reference/keywords/for) pętli tego zmniejsza zmienna pętli po każdej iteracji.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|if|Tworzy [Jeśli](/dotnet/csharp/language-reference/keywords/if-else) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|Indeksator|Tworzy deklaracji indeksatora.|Wewnątrz klasy lub struktury.|
|interface|Tworzy [interfejsu](/dotnet/csharp/language-reference/keywords/interface) deklaracji.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|wywołania|Tworzy blok, który bezpiecznie wywołuje zdarzenie.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|iterator|Tworzy iterator.|Wewnątrz klasy lub struktury.|
|iterindex|Tworzy "o nazwie" pary iteratora i indeksatora przy użyciu klasy zagnieżdżonej.|Wewnątrz klasy lub struktury.|
|lock|Tworzy [blokady](/dotnet/csharp/language-reference/keywords/lock-statement) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|mbox|Tworzy wywołanie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Może być konieczne dodanie odwołania do *System.Windows.Forms.dll*.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|— przestrzeń nazw|Tworzy [przestrzeni nazw](/dotnet/csharp/language-reference/keywords/namespace) deklaracji.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw).|
|Prop|Tworzy [automatycznie implementowana właściwość](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) deklaracji.|Wewnątrz klasy lub struktury.|
|propfull|Tworzy oświadczenie właściwości z `get` i `set` metod dostępu.|Wewnątrz klasy lub struktury.|
|propg|Tworzy tylko do odczytu [automatycznie implementowana właściwość](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) za pomocą prywatnej `set` metody dostępu.|Wewnątrz klasy lub struktury.|
|SIM|Tworzy [statyczne](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) deklaracji metody Main.|Wewnątrz klasy lub struktury.|
|struktura |Tworzy [struktury](/dotnet/csharp/language-reference/keywords/struct) deklaracji.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|svm|Tworzy [statyczne](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void) deklaracji metody Main.|Wewnątrz klasy lub struktury.|
|— przełącznik|Tworzy [Przełącz](/dotnet/csharp/language-reference/keywords/switch) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|Wypróbuj|Tworzy [try-catch —](/dotnet/csharp/language-reference/keywords/try-catch) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|tryf|Tworzy [try-finally](/dotnet/csharp/language-reference/keywords/try-finally) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|unchecked|Tworzy [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|unsafe|Tworzy [niebezpieczne](/dotnet/csharp/language-reference/keywords/unsafe) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|
|korzystanie|Tworzy [przy użyciu](/dotnet/csharp/language-reference/keywords/using-directive) dyrektywy.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw).|
|while|Tworzy [podczas](/dotnet/csharp/language-reference/keywords/while) pętli.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|

## <a name="see-also"></a>Zobacz także

- [Funkcje fragmentów kodu](../ide/code-snippet-functions.md)
- [Fragmenty kodu](../ide/code-snippets.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Instrukcje: Użycie fragmentów kodu polecenia Otocz przez](../ide/how-to-use-surround-with-code-snippets.md)