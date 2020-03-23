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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1739d6b2376a4f86edd3c0102f7fad79da5d7cd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568623"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Używanie wyrażeń regularnych w programie Visual Studio

Visual Studio używa [wyrażeń regularnych platformy .NET](/dotnet/standard/base-types/regular-expressions) do znajdowania i zastępowania tekstu.

## <a name="regular-expression-examples"></a>Przykłady wyrażeń regularnych

Poniższa tabela zawiera kilka znaków wyrażeń regularnych, operatorów, konstrukcji i przykładów wzorca. Aby uzyskać pełniejszy odnośnik, zobacz [Język wyrażenia regularnego](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Przeznaczenie|Wyrażenie|Przykład|
|-------------|----------------|-------------|
|Dopasuj dowolny pojedynczy znak (z wyjątkiem podziału wiersza). Aby uzyskać więcej informacji, zobacz [Dowolny znak](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o`pasuje do "aro" w "around" i "abo" w "o", ale nie "acro" w "across"|
|Dopasuj zero lub więcej wystąpień poprzedniego wyrażenia (dopasować jak najwięcej znaków, jak to możliwe). Aby uzyskać więcej informacji, zobacz [Dopasowywuj zero lub więcej razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r`pasuje do "r" w "rack", "ar" w "ark", i "aar" w "aardvark"|
|Dopasuj dowolny znak zero lub więcej razy.|.*|`c.*e`dopasowuje "cke" w "rakieta", "comme" w "komentarz" i "kod" w "kod"|
|Dopasuj jedno lub więcej wystąpień poprzedniego wyrażenia (dopasować jak najwięcej znaków, jak to możliwe). Aby uzyskać więcej informacji, zobacz [Dopasowyj jeden lub więcej razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e+d`pasuje do "eed" w "podajniku" i "ed" w "wyblakłe"|
|Dopasuj dowolny znak jeden lub więcej razy.|.+|`e.+e`pasuje do "eede" w "feeder", ale nie znajduje żadnych dopasowań w "feed"|
|Dopasuj zero lub więcej wystąpień poprzedniego wyrażenia (dopasować jak najmniej znaków, jak to możliwe). Aby uzyskać więcej informacji, zobacz [Dopasowywzerić zero lub więcej razy (dopasowanie z opóźnieniem).](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-)|*?|`\w*?d`pasuje do "fad" i "ed" w "wyblakłe", ale nie całe słowo "wyblakłe" ze względu na leniwy mecz|
|Dopasuj jedno lub więcej wystąpień poprzedniego wyrażenia (dopasować jak najmniej znaków, jak to możliwe). Aby uzyskać więcej informacji, zobacz [Dopasowyj jeden lub więcej razy (dopasowanie z opóźnieniem)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?`pasuje do "ee" w "asleep" i "ed" w "wyblakłe", ale nie znajduje żadnych zapałek w "fade"|
|Zakotwiczenie ciągu dopasowania na [początku linii lub ciągu](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car`pasuje do słowa "samochód" tylko wtedy, gdy pojawia się na początku wiersza|
|Zakotwiczenie ciągu dopasowania do [końca wiersza](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r?$|`car\r?$`pasuje do "samochodu" tylko wtedy, gdy pojawia się na końcu linii|
|Zakotwiczenie ciągu dopasowania na końcu pliku|$|`car$`dopasowuje "samochód" tylko wtedy, gdy pojawia się na końcu pliku|
|Dopasowywuj dowolny pojedynczy znak w zestawie|[abc]|`b[abc]`pasuje do "ba", "bb" i "bc"|
|Dopasowyuj dowolną postać w zakresie znaków|[a-f]|`be[n-t]`pasuje do "zakładu" w "między", "ben" w "poniżej" i "bes" w "obok", ale nie znajduje żadnych meczów w "poniżej"|
|Przechwytywanie i niejawnie numer wyrażenia zawartego w nawiasie|()|`([a-z])X\1`pasuje do "aXa" i "bXb", ale nie "aXb". "\1" odnosi się do pierwszej grupy wyrażeń "[a-z]". Aby uzyskać więcej informacji, zobacz [Przechwytywanie grup i wzorców zastępczych](#capture-groups-and-replacement-patterns). |
|Unieważnienie dopasowania|(?! abc)|`real(?!ity)`pasuje do "prawdziwych" w "realty" i "naprawdę", ale nie w "rzeczywistości". Znajduje również drugi "prawdziwy" (ale nie pierwszy "prawdziwy") w "realityreal".|
|Dopasuj dowolny znak, który nie znajduje się w danym zestawie znaków. Aby uzyskać więcej informacji, zobacz [Grupa znaków negatywnych](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^abc]|`be[^n-t]`pasuje do "bef" w "before", "beh" w "behind" i "bel" w "poniżej", ale nie znajduje żadnych dopasowań w "poniżej"|
|Dopasowywuj wyrażenie przed lub po symbolu|&#124;|`(sponge|mud) bath`pasuje do "kąpieli gąbkowej" i "kąpieli błotnej"|
|[Ucieczka od postaci](/dotnet/standard/base-types/character-escapes-in-regular-expressions) po ukośniku odwrotnym| \\ |`\^`pasuje do znaku ^|
|Określ liczbę wystąpień poprzedniego znaku lub grupy. Aby uzyskać więcej informacji, zobacz [Dopasowyj dokładnie n razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, gdzie 'n' jest liczbą wystąpień|`x(ab){2}x`pasuje do "xababx"<br/>`x(ab){2,3}x`pasuje do "xababx" i "xabababx", ale nie "xababababx"|
|[Dopasuj tekst w kategorii Unicode](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Aby uzyskać więcej informacji na temat klas znaków Unicode, zobacz [Właściwości znaków Standard Unicode 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, gdzie "X" jest numerem Unicode.|`\p{Lu}`pasuje do "T" i "D" w "Thomas Doe"|
|[Dopasowywuj granicę wyrazu](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (Poza klasą `\b` znaków określa granicę wyrazu, `\b` a wewnątrz klasy znaków określa backspace.)|`\bin`pasuje "in" w "inside", ale nie znajdzie meczów w "pinto"|
|Dopasowywuj podział wiersza (czyli zwrot karetki, po którym następuje nowy wiersz)|\r?\n|`End\r?\nBegin`dopasowuje "End" i "Begin" tylko wtedy, gdy "End" jest ostatnim ciągiem w wierszu, a "Begin" jest pierwszym ciągiem w następnym wierszu|
|Dopasowyj dowolny [znak wyrazu](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd`dopasowuje "add" i "a1d", ale nie "a d"|
|Dopasowyuj dowolny [znak odstępu](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface`pasuje do wyrażenia "Interfejs publiczny"|
|Dopasowyj dowolny [znak cyfry dziesiętnej](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d`pasuje do "4" i "0" w "wd40"|

Przykładowe wyrażenie regularne, które łączy niektóre operatory i konstrukcje, aby `\b0[xX]([0-9a-fA-F]+\)\b`dopasować liczbę szesnastkową jest . To wyrażenie pasuje do "0xc67f", ale nie "0xc67g".

> [!TIP]
> W systemach operacyjnych Windows większość wierszy kończy się na "\r\n" (zwrot karetki, po którym następuje nowy wiersz). Te znaki nie są widoczne, ale są obecne w edytorze i przekazywane do usługi wyrażeń regularnych .NET.

## <a name="capture-groups-and-replacement-patterns"></a>Przechwytywanie grup i wzorców zastępczych

Grupa przechwytywania wyznacza wyrażenie podrzędne wyrażenia regularnego i przechwytuje podciąg ciągu wejściowego. Przechwycone grupy można użyć w samym wyrażeniu regularnym (na przykład w celu wyszukania powtarzającego się wyrazu) lub wzorca zastępczego. Aby uzyskać szczegółowe informacje, zobacz [Grupowanie konstrukcji w wyrażeniach regularnych](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Aby utworzyć ponumerowane grupy przechwytywania, otoczyć wyrażenie podrzędne nawiasami we wzorcu wyrażenia regularnego. Przechwytuje są numerowane automatycznie od lewej do prawej na podstawie położenia nawiasu otwarcia w wyrażeniu regularnym. Aby uzyskać dostęp do przechwyconej grupy:

- **w ramach wyrażenia** `\number`regularnego : Użyj . Na przykład `\1` w wyrażeniu `(\w+)\s\1` regularnym `(\w+)`odwołuje się do pierwszej grupy przechwytywania .

- **w wzorze zastępczym**: Użyj `$number`. Na przykład zgrupowane `(\d)([a-z])` wyrażenie regularne definiuje dwie grupy: pierwsza grupa zawiera pojedynczą cyfrę dziesiętną, a druga grupa zawiera pojedynczy znak między **a** i **z**. Wyrażenie znajduje cztery dopasowania w następującym ciągu: **1a 2b 3c 4d**. Ciąg `z$1` zastępczy odwołuje się tylko`$1`do pierwszej grupy ( ) i konwertuje ciąg na **z1 z2 z3 z4**.

Na poniższej ilustracji `(\w+)\s\1` przedstawiono `$1`wyrażenie regularne i ciąg zastępczy . Zarówno wyrażenie regularne, jak i wzorzec zastępczy odwołują się do pierwszej grupy przechwytywania, która jest automatycznie numerowana 1. Po **wybraniu opcji Zamień wszystko** w oknie dialogowym **Szybkie zamienianie** w programie Visual Studio powtarzające się słowa są usuwane z tekstu.

![Szybkie zastępowanie z numerowanymi grupami przechwytywania w programie Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Upewnij się, że w oknie dialogowym **Szybkie zamienianie** jest zaznaczony przycisk **Użyj wyrażeń** regularnych.

### <a name="named-capture-groups"></a>Nazwane grupy przechwytywania

Zamiast polegać na automatycznej numerowaniu grupy przechwytywania, można nadać jej nazwę. Składnia nazwanej grupy przechwytywania `(?<name>subexpression)`to .

Nazwane grupy przechwytywania, takie jak ponumerowane grupy przechwytywania, mogą być używane w samym wyrażeniu regularnym lub we wzorcu zastępczym. Aby uzyskać dostęp do nazwanej grupy przechwytywania:

- **w ramach wyrażenia** `\k<name>`regularnego : Użyj . Na przykład `\k<repeated>` w wyrażeniu `(?<repeated>\w+)\s\k<repeated>` regularnym odwołuje się `repeated` do grupy przechwytywania, która jest nazwana i której podwyrażenie jest `\w+`.

- **w wzorze zastępczym**: Użyj `${name}`. Na przykład `${repeated}`.

Na przykład na poniższej ilustracji `(?<repeated>\w+)\s\k<repeated>` przedstawiono `${repeated}`wyrażenie regularne i ciąg zastępczy . Zarówno wyrażenie regularne, jak i wzorzec zastępczy odwołują się do grupy przechwytywania o nazwie `repeated`. Po **wybraniu opcji Zamień wszystko** w oknie dialogowym **Szybkie zamienianie** w programie Visual Studio powtarzające się słowa są usuwane z tekstu.

![Szybkie zastępowanie przedstawiające nazwaną grupę przechwytywania w programie Visual Studio](media/named-capture-group.png)

> [!TIP]
> Upewnij się, że w oknie dialogowym **Szybkie zamienianie** jest zaznaczony przycisk **Użyj wyrażeń** regularnych.

Aby uzyskać więcej informacji na temat nazwanych grup przechwytywania, zobacz [Nazwane dopasowane podwyrażenia](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Aby uzyskać więcej informacji na temat wyrażeń regularnych używanych w wzorcach zastępczych, zobacz [Podstawienia w wyrażeniach regularnych](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Zobacz też

- [Język wyrażenia regularnego](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
