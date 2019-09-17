---
title: Użyj wyrażeń regularnych
ms.date: 09/13/2019
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
ms.openlocfilehash: 380201259cc19c15b68ea9142308f21b901a9241
ms.sourcegitcommit: b02c40c1ba193e38b5ace14590a6d57590d3270f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2019
ms.locfileid: "71012584"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Używanie wyrażeń regularnych w programie Visual Studio

Program Visual Studio używa [wyrażeń regularnych programu .NET](/dotnet/standard/base-types/regular-expressions) do znajdowania i zastępowania tekstu.

## <a name="regular-expression-examples"></a>Przykłady wyrażeń regularnych

Poniższa tabela zawiera niektóre znaki wyrażenia regularnego, operatory, konstrukcje i przykłady wzorców. Aby uzyskać bardziej szczegółowe informacje, zobacz [Język wyrażeń regularnych](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Cel|Wyrażenie|Przykład|
|-------------|----------------|-------------|
|Dopasowuje dowolny pojedynczy znak (poza podziałem wiersza). Aby uzyskać więcej informacji, zobacz [dowolny znak](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o`Dopasowuje "ARO" w "dookoła" i "abo" w "about", ale nie "Acro" w "w"|
|Dopasowuje zero lub więcej wystąpień poprzedniego wyrażenia (dopasowuje tyle znaków jak to możliwe). Aby uzyskać więcej informacji, zobacz [dopasowanie zero lub więcej razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r` pasuje "r" w "rack", "ar" w "ark" i "aar" w "aardvark"|
|Dopasowuje dowolny znak zero lub więcej razy.|.*|`c.*e` pasuje do "cke" w "racket", "comme" w "comment" i "code" w "code"|
|Dopasowuje jedno lub więcej wystąpień poprzedniego wyrażenia (dopasowuje dowolną liczbę znaków, jak to możliwe). Aby uzyskać więcej informacji, zobacz [dopasowanie jeden lub więcej razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e+d`Dopasowuje "EED" w "podajniku" i "Ed" w "wyblakł"|
|Dopasowuje dowolny znak jeden lub więcej razy.|.+|`e.+e`Dopasowuje "eede" w "podajniku", ale nie znajduje żadnych dopasowań w "kanale"|
|Dopasowuje zero lub więcej wystąpień poprzedniego wyrażenia (dopasowuje się jak najmniejsza liczba znaków). Aby uzyskać więcej informacji, zobacz [dopasowanie zero lub więcej razy (dopasowanie z opóźnieniem)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`\w*?d`Dopasowuje "FAD" i "Ed" w "wyblakłe", ale nie cały wyraz "wyblakł" ze względu na dopasowanie z opóźnieniem|
|Dopasowuje jedno lub więcej wystąpień poprzedniego wyrażenia (dopasowanie możliwie najmniejszej liczby znaków). Aby uzyskać więcej informacji, zobacz [dopasowanie jeden lub więcej razy (dopasowanie z opóźnieniem)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?`Dopasowuje "ee" w "uśpieniu" i "Ed" w "wyblakł", ale nie znajduje żadnych dopasowań w "zaniku"|
|Zakotwiczenie ciągu dopasowania do [początku wiersza lub ciągu](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car`dopasowuje wyraz "samochód" tylko wtedy, gdy pojawia się na początku wiersza|
|Zakotwiczenie ciągu dopasowania do [końca wiersza](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r?$|`car\r?$`Dopasowuje "samochód" tylko wtedy, gdy pojawia się na końcu wiersza|
|Zakotwiczenia ciągu dopasowania na końcu pliku|$|`car$`Dopasowuje "samochód" tylko wtedy, gdy pojawia się na końcu pliku|
|Dopasuj jeden dowolny znak, które są dostępne w zestawie|[abc]|`b[abc]`Dopasowuje "BA", "bb" i "BC"|
|Dopasuj dowolny znak zakresu znaków|[a-f]|`be[n-t]`Dopasowuje "trafienie" w "Between", "Ben" w "pod" i "BES" w "obok", ale nie znajduje żadnych dopasowań w "poniżej"|
|Przechwytywanie i niejawne numerowanie wyrażenia zawartgoe w nawiasach|()|`([a-z])X\1` pasuje "do aXa" i "bXb", ale nie "aXb". "\1" odnosi się do pierwszej grupy wyrażenie "[a-z]". Aby uzyskać więcej informacji, zobacz [Przechwytywanie grup i wzorców](#capture-groups-and-replacement-patterns)zastąpień. |
|Unieważnienie dopasowania|(?! ABC)|`real(?!ity)` pasuje do członu "real" w słowach "realty" i "really", ale nie w "reality". W "realityreal" danych znajdzie także drugi "prawdziwy" (ale nie pierwszy "prawdziwy").|
|Dopasowuje dowolny znak, który nie znajduje się w danym zestawie znaków. Aby uzyskać więcej informacji, zobacz [Grupa znaków negatywnych](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^ abc]|`be[^n-t]`dopasowuje wartość "BEF" w "Before", "BEH" w "za" i "etykiety" w "poniżej", ale nie znajduje żadnych dopasowań w "poniżej"|
|Dopasowuje wyrażenie przed lub po symbolu|&#124;|`(sponge|mud) bath`Dopasowuje "kąpiel gąbki" i "kąpiel Mud"|
|[Znak ucieczki](/dotnet/standard/base-types/character-escapes-in-regular-expressions) po ukośniku odwrotnym| \\ |`\^`Dopasowuje znak ^|
|Określ liczbę wystąpień poprzedzającego znaku lub grupy. Aby uzyskać więcej informacji, zobacz [dopasowanie dokładnie n razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, gdzie "n" jest liczbą wystąpień|`x(ab){2}x`pasuje do "xababx"<br/>`x(ab){2,3}x`Dopasowuje "xababx" i "xabababx", ale nie "xababababx"|
|[Dopasowuje tekst w kategorii Unicode](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Aby uzyskać więcej informacji na temat klas znaków Unicode, zobacz [Unicode Standard 5,2 Properties](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, gdzie "X" jest numerem kodu Unicode.|`\p{Lu}`Dopasowuje "T" i "D" w "Thomas Nowak"|
|[Dopasowuje granicę słowa](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (poza klasą znak `\b` określa granicy słowa i wewnątrz znak klasy `\b` określa backspace.)|`\bin`Dopasowuje "in" w "wewnątrz", ale nie znajduje żadnych dopasowań w "Pinto"|
|Dopasowuje podział wiersza (oznacza to, że znak powrotu karetki następuje po nowym wierszu)|\r?\n|`End\r?\nBegin`Dopasowuje "End" i "BEGIN" tylko wtedy, gdy "koniec" jest ostatnim ciągiem w wierszu i "BEGIN" jest pierwszym ciągiem w następnym wierszu|
|Dopasowuje dowolny [znak słowa](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd`Dopasowuje "Add" i "A1d", ale nie "a d"|
|Dopasowuje dowolny [znak odstępu](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface`Dopasowuje frazę "interfejs publiczny"|
|Dopasowuje dowolny [znak cyfry dziesiętnej](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d`Dopasowuje "4" i "0" w "WD40"|

Przykładowe wyrażenie regularne, które łączy niektóre operatory i konstrukcje, aby odpowiadało liczbie `\b0[xX]([0-9a-fA-F]+\)\b`szesnastkowej. To wyrażenie pasuje do "0xc67f", ale nie "0xc67g".

> [!TIP]
> W systemach operacyjnych Windows większość linii kończyć się "\r\n" (znak powrotu karetki następuje nowy wiersz). Te znaki nie są widoczne, ale są obecne w edytorze i przechodzą do usługi wyrażeń regularnych programu .NET.

## <a name="capture-groups-and-replacement-patterns"></a>Przechwyć grupy i wzorce zastępujące

Grupa przechwytywania wyznacza Podwyrażenie wyrażenia regularnego i przechwytuje podciąg ciągu wejściowego. Przechwyconych grup można użyć w wyrażeniu regularnym (na przykład w celu wyszukania Powtórzonego słowa) lub w wzorcu zastępczym. Aby uzyskać szczegółowe informacje, zobacz [grupowanie konstrukcji w wyrażeniach regularnych](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Aby utworzyć numerowaną grupę przechwytywania, umieść Podwyrażenie z nawiasami we wzorcu wyrażenia regularnego. Przechwytywanie są numerowane automatycznie od lewej do prawej w oparciu o pozycję nawiasu otwierającego w wyrażeniu regularnym. Aby uzyskać dostęp do przechwyconej grupy:

- **w wyrażeniu regularnym**: Użyj `\number`. Na przykład, `\1` w wyrażeniu `(\w+)\s\1` regularnym odwołuje się do `(\w+)`pierwszej grupy przechwytywania.

- **w wzorcu wymiany**: Użyj `$number`. Na przykład grupowanych wyrażenia regularnego `(\d)([a-z])` definiuje dwie grupy: pierwsza grupa zawiera pojedynczą cyfrą dziesiętną, a drugiej grupy pojedynczy znak między **a** i **z**. Wyrażenie umożliwia znalezienie czterech dopasowań w następującym ciągu: **1a 2b 3C 4D**. Ciąg `z$1` zamienny odwołuje się tylko do pierwszej`$1`grupy () i konwertuje ciąg na **Z1 Z2 Z3 Z4**.

Na poniższej ilustracji przedstawiono wyrażenie `(\w+)\s\1` regularne i ciąg `$1`zastępczy. Zarówno wyrażenie regularne, jak i wzorzec zastępczy odwołują się do pierwszej grupy przechwytywania, która jest automatycznie numerowana 1. Po wybraniu opcji **Zamień wszystkie** w oknie dialogowym **szybkie zamienianie** w programie Visual Studio powtórzone słowa są usuwane z tekstu.

![Szybkie zastępowanie przedstawiające numerowaną grupę przechwytywania w programie Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Upewnij się, że w oknie dialogowym **szybkie zamienianie** jest zaznaczone pole wyboru **Użyj wyrażeń regularnych** .

### <a name="named-capture-groups"></a>Nazwane grupy przechwytywania

Zamiast polegać na automatycznym numerowaniu grupy przechwytywania, można nadać jej nazwę. Składnia nazwanej grupy przechwytywania to `(?<name>subexpression)`.

Nazwane grupy przechwytywania, takie jak numerowane grupy przechwytywania, mogą być używane wewnątrz wyrażenia regularnego lub w wzorcu zamiennym. Aby uzyskać dostęp do nazwanej grupy przechwytywania:

- **w wyrażeniu regularnym**: Użyj `\k<name>`. Na przykład `\k<repeated>` w wyrażeniu `(?<repeated>\w+)\s\k<repeated>` regularnym odwołuje się do grupy przechwytywania o `repeated` nazwie i której Podwyrażenie `\w+`ma wartość.

- **w wzorcu wymiany**: Użyj `${name}`. Na przykład `${repeated}`.

Na przykład na poniższej ilustracji przedstawiono wyrażenie `(?<repeated>\w+)\s\k<repeated>` regularne i ciąg `${repeated}`zastępczy. Zarówno wyrażenie regularne, jak i zastępczy wzorzec odwołują się do `repeated`grupy przechwytywania o nazwie. Po wybraniu opcji **Zamień wszystkie** w oknie dialogowym **szybkie zamienianie** w programie Visual Studio powtórzone słowa są usuwane z tekstu.

![Szybkie zastępowanie przedstawiające nazwaną grupę przechwytywania w programie Visual Studio](media/named-capture-group.png)

> [!TIP]
> Upewnij się, że w oknie dialogowym **szybkie zamienianie** jest zaznaczone pole wyboru **Użyj wyrażeń regularnych** .

Aby uzyskać więcej informacji na temat nazwanych grup przechwytywania, zobacz [nazwane Podwyrażenie dopasowane](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Aby uzyskać więcej informacji na temat wyrażeń regularnych, które są używane w wzorcach zamiennych, zobacz [podstawienia w wyrażeniach regularnych](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
