---
title: Użyj wyrażeń regularnych
ms.date: 03/26/2018
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b20cf3692cf76f602eb11b0a53a1669c919f1679
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043570"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Używanie wyrażeń regularnych w programie Visual Studio

Program Visual Studio używa [wyrażeń regularnych programu .NET](/dotnet/standard/base-types/regular-expressions) do znajdowania i zamieniania tekstu.

## <a name="regular-expression-examples"></a>Przykłady wyrażeń regularnych

Poniższe tabele zawiera znaki wyrażenia regularnego, operatory, konstrukcje i przykłady wzorca. Aby pełniejsze informacje, zobacz [język wyrażeń regularnych](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Cel|Wyrażenie|Przykład|
|-------------|----------------|-------------|
|Dopasowuje dowolny pojedynczy znak (oprócz podziału wiersza). Aby uzyskać więcej informacji, zobacz [dowolny znak](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o` pasuje "aro" w "around" i "abo" w "about" ale nie "acro" w "w".|
|Dopasowuje zero lub więcej wystąpień poprzedniego wyrażenia (dopasowuje tak dużą liczbę znaków, jak to możliwe). Aby uzyskać więcej informacji, zobacz [dopasowuje zero lub więcej razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r` pasuje "r" w "rack", "ar" w "ark" i "aar" w "aardvark"|
|Dopasowuje dowolny znak zero lub więcej razy (symbol wieloznaczny \*)|.*|`c.*e` pasuje do "cke" w "racket", "comme" w "comment" i "code" w "code"|
|Pasuje jedno lub więcej wystąpień poprzedniego wyrażenia (dopasowuje tak dużą liczbę znaków, jak to możliwe). Aby uzyskać więcej informacji, zobacz [Dopasuj jeden lub więcej razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e.+d` pasuje do "eed" w "feeder" ale nie "ed".|
|Dopasowuje dowolny znak jeden lub więcej razy (symbol wieloznaczny?)|.+|`e.+e` pasuje do "eede" w "feeder" ale nie "ee".|
|Dopasowuje zero lub więcej wystąpień poprzedniego wyrażenia (dopasowuje tak małą znaków, jak to możliwe). Aby uzyskać więcej informacji, zobacz [dopasowania zero lub więcej razy (dopasowanie z opóźnieniem)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`e.*?e` pasuje do "ee" w "feeder" ale nie do "eede".|
|Pasuje jedno lub więcej wystąpień poprzedniego wyrażenia (dopasowuje tak małą znaków, jak to możliwe). Aby uzyskać więcej informacji, zobacz [dopasować jeden lub więcej razy (dopasowanie z opóźnieniem)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e.+?e` pasuje "do ente" i "erprise" w "enterprise", ale nie całego słowa "enterprise".|
|Zakotwiczenia ciągu dopasowania do [początek wiersza lub ciągu](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car` Dopasowuje słowa "samochód" tylko wtedy, gdy pojawia się na początku wiersza.|
|Zakotwiczenia ciągu dopasowania do [koniec wiersza](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r?$|`end\r?$` pasuje do "end" tylko wtedy, gdy pojawia się na końcu wiersza.|
|Zakotwiczenia ciągu dopasowania na końcu pliku|$|`end$` pasuje do "end" tylko wtedy, gdy pojawia się na końcu pliku.|
|Dopasuj jeden dowolny znak, które są dostępne w zestawie|[abc]|`b[abc]` pasuje do "ba", "bb" i "bc".|
|Dopasuj dowolny znak zakresu znaków|[a-f]|`be[n-t]` Dopasowuje "bet" w "between", "ben" w "beneath" i "bes" w "beside", ale nie "below".|
|Przechwytywanie i niejawne numerowanie wyrażenia zawartgoe w nawiasach|()|`([a-z])X\1` pasuje "do aXa" i "bXb", ale nie "aXb". "\1" odnosi się do pierwszej grupy wyrażenie "[a-z]".|
|Unieważnienie dopasowania|(?! ABC)|`real(?!ity)` pasuje do członu "real" w słowach "realty" i "really", ale nie w "reality". W "realityreal" danych znajdzie także drugi "prawdziwy" (ale nie pierwszy "prawdziwy").|
|Dopasowuje dowolny znak, który nie znajduje się w danym zestawie znaków. Aby uzyskać więcej informacji, zobacz [grupa znaków negatywnych](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^ abc]|`be[^n-t]` pasuje "do bef" w "przed", "beh" w "za" i "bel" w "below", ale nie "beneath".|
|Dopasowuje wyrażenie przed lub po symbolu|&#124;|`(sponge\|mud) bath` pasuje "sponge bath" i "mud bath."|
|[Znak ucieczki](/dotnet/standard/base-types/character-escapes-in-regular-expressions) po ukośniku odwrotnym| \\ |`\^` pasuje do znaku ^.|
|Określ liczbę wystąpień poprzedzającego znaku lub grupy. Aby uzyskać więcej informacji, zobacz [odpowiada dokładnie n razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, gdzie "n" to liczba wystąpień|`x(ab){2}x` odpowiada "xababx" i `x(ab){2,3}x` odpowiada "xababx" i "xabababx", ale nie "xababababx".|
|[Dopasowuje tekst w kategorii Unicode](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Aby uzyskać więcej informacji dotyczących klas znaków Unicode, zobacz [właściwości znaków standardu Unicode standardowe 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, gdzie "X" jest numerem kodu Unicode.|`\p{Lu}` pasuje do "T" i "D" w "Thomas Doe".|
|[Dopasuj granicę wyrazu](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (poza klasą znak `\b` określa granicy słowa i wewnątrz znak klasy `\b` określa backspace.)|`\bin` pasuje do "w" w "wewnątrz" ale nie "pinto".|
|Dopasuj podział wiersza (czyli znak powrotu karetki następuje nowy wiersz)|\r?\n|`End\r?\nBegin` pasuje do "Koniec" i "Początek" tylko wtedy, gdy "Koniec" jest ostatnim ciągiem w wierszu a "Początek" jest pierwszym ciągiem w następnym wierszu.|
|Pasuje do żadnego [znak wyrazu](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd` Dopasowuje "add" i "a1d" ale nie "d".|
|Pasuje do żadnego [biały znak](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface` pasuje do frazy "Interfejs publiczny".|
|Pasuje do żadnego [znak cyfry dziesiętnej](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d` pasuje i "3" w "3456", "2" w 23" i"1"w"1".|
|Dopasowuje znak Unicode|\uXXXX gdzie XXXX określa wartość znaku Unicode.|`\u0065` Dopasowuje znak "e".|
|Dopasuj identyfikator|\b [\_\w-[0-9]] [\_\w]*\b|Dopasowuje "type1", ale nie "& type1" lub "#define".|
|Dopasuj ciąg w cudzysłowie|((\\".+?\\")&#124;('.+?'))|Dopasowuje dowolny ciąg w pojedynczym lub podwójnym cudzysłowie.|
|Dopasuj liczbę szesnastkową|\b0[xX]([0-9a-fA-F]+\)\b|Dopasowuje "0xc67f", ale nie "0xc67g".|
|Dopasuj liczby całkowite i miejsca dziesiętne|\b[0-9]*\\.\*[0-9]+\b|Dopasowuje "1,333".|

> [!TIP]
> W systemach operacyjnych Windows większość linii kończyć się "\r\n" (znak powrotu karetki następuje nowy wiersz). Te znaki nie są widoczne, ale są obecne w edytorze i są przekazywane do usługi wyrażenie regularne .NET.

## <a name="capture-groups-and-replacement-patterns"></a>Grupy przechwytywania i wzorce zamieniania

Grupa przechwytywania wyznacza podwyrażenia wyrażeń regularnych i przechwytuje podciągu ciągu wejściowego. Można użyć przechwyconych grupach w wyrażeniach regularnych, sama (na przykład, aby wyszukać powtarzające się wyrazy), lub we wzorcu zamieniania. Aby uzyskać szczegółowe informacje, zobacz [grupowania konstrukcje w wyrażeniach regularnych](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Aby utworzyć grupę przechwytywania numerowaną, należy ująć Podwyrażenie przy użyciu nawiasów we wzorcu wyrażenia regularnego. Przechwytywania są automatycznie numerowane od lewej do prawej strony, na podstawie pozycji nawiasu otwierającego w wyrażeniu regularnym. Dostęp do przechwyconej grupy:

- **w wyrażeniach regularnych**: Użyj `\number`. Na przykład `\1` w wyrażeniu regularnym `(\w+)\s\1` odwołuje się do pierwszej grupy przechwytywania `(\w+)`.

- **we wzorcu zamieniania znak**: Użyj `$number`. Na przykład grupowanych wyrażenia regularnego `(\d)([a-z])` definiuje dwie grupy: pierwsza grupa zawiera pojedynczą cyfrą dziesiętną, a drugiej grupy pojedynczy znak między **a** i **z**. Wyrażenie wyszukuje cztery dopasowań w następujący ciąg: **1a 2b 3c 4d**. Ciąg zastępujący `z$1` odwołuje się do pierwszej grupy (`$1`) i konwertuje ciąg na **z1 z2 z3 z4**.

Na poniższej ilustracji przedstawiono wyrażenia regularnego `(\w+)\s\1` i ciąg zastępujący `$1`. Wyrażenia regularnego i wzorzec zamieniania odwoływać się do pierwszej grupy przechwytywania, automatycznie numerowanych 1. Po wybraniu **Zamień wszystkie** w **szybkiego zamieniania** okno dialogowe w programie Visual Studio, należy powtórzyć wyrazy są usuwane z powieści.

![Szybkie zamienianie przedstawiający grupa przechwytywania numerowanej w programie Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Upewnij się, że **Użyj wyrażeń regularnych** przycisk jest zaznaczony w **szybkiego zamieniania** okno dialogowe.

### <a name="named-capture-groups"></a>Funkcji przechwytywania o nazwie grupy

Zamiast polegania na automatycznego numerowania grupy przechwytywania, możesz nadać mu nazwę. Składnia dla funkcji przechwytywania o nazwie grupy jest `(?<name>subexpression)`.

Nazwanych grup przechwytywania, takich jak numerowanych grup przechwytywania, może być używany w wyrażeniu regularnym, samego lub we wzorcu zamieniania. Aby uzyskać dostęp do grupy funkcji przechwytywania o nazwie:

- **w wyrażeniach regularnych**: Użyj `\k<name>`. Na przykład `\k<repeated>` w wyrażeniu regularnym `(?<repeated>\w+)\s\k<repeated>` odwołuje się do grupy przechwytywania, który nosi nazwę `repeated` i którego cząstkowe jest `\w+`.

- **we wzorcu zamieniania znak**: Użyj `${name}`. Na przykład `${repeated}`.

Na przykład na poniższej ilustracji przedstawiono wyrażenia regularnego `(?<repeated>\w+)\s\k<repeated>` i ciąg zastępujący `${repeated}`. Wyrażenia regularnego i wzorzec zamieniania odwołują się do grupy przechwytywania o nazwie `repeated`. Po wybraniu **Zamień wszystkie** w **szybkiego zamieniania** okno dialogowe w programie Visual Studio, należy powtórzyć wyrazy są usuwane z powieści.

![Szybkie zamienianie przedstawiający funkcji przechwytywania o nazwie grupy w programie Visual Studio](media/named-capture-group.png)

> [!TIP]
> Upewnij się, że **Użyj wyrażeń regularnych** przycisk jest zaznaczony w **szybkiego zamieniania** okno dialogowe.

Aby uzyskać więcej informacji na temat funkcji przechwytywania o nazwie grup, zobacz [o nazwie dopasowane podwyrażenia](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Aby uzyskać więcej informacji na temat wyrażeń regularnych, które są używane we wzorcach zamieniania, zobacz [podstawienia w wyrażeniach regularnych](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
