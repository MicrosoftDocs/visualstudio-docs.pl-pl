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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568623"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Używanie wyrażeń regularnych w programie Visual Studio

Program Visual Studio używa [wyrażeń regularnych programu .NET](/dotnet/standard/base-types/regular-expressions) do znajdowania i zastępowania tekstu.

## <a name="regular-expression-examples"></a>Przykłady wyrażeń regularnych

Poniższa tabela zawiera niektóre znaki wyrażenia regularnego, operatory, konstrukcje i przykłady wzorców. Aby uzyskać bardziej szczegółowe informacje, zobacz [Język wyrażeń regularnych](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Cel|Wyrażenie|Przykład|
|-------------|----------------|-------------|
|Dopasowuje dowolny pojedynczy znak (poza podziałem wiersza). Aby uzyskać więcej informacji, zobacz [dowolny znak](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o` dopasowuje "ARO" w "dookoła" i "abo" w "about", ale nie "Acro" w "w"|
|Dopasowuje zero lub więcej wystąpień poprzedniego wyrażenia (dopasowuje tyle znaków jak to możliwe). Aby uzyskać więcej informacji, zobacz [dopasowanie zero lub więcej razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r` pasuje "r" w "rack", "ar" w "ark" i "aar" w "aardvark"|
|Dopasowuje dowolny znak zero lub więcej razy.|.*|`c.*e` pasuje do "cke" w "racket", "comme" w "comment" i "code" w "code"|
|Dopasowuje jedno lub więcej wystąpień poprzedniego wyrażenia (dopasowuje dowolną liczbę znaków, jak to możliwe). Aby uzyskać więcej informacji, zobacz [dopasowanie jeden lub więcej razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e+d` pasuje do "EED" w "podajniku" i "Ed" w "wyblakł"|
|Dopasowuje dowolny znak jeden lub więcej razy.|.+|`e.+e` pasuje do "eede" w "podajniku", ale nie znajduje żadnych dopasowań w "kanale"|
|Dopasowuje zero lub więcej wystąpień poprzedniego wyrażenia (dopasowuje się jak najmniejsza liczba znaków). Aby uzyskać więcej informacji, zobacz [dopasowanie zero lub więcej razy (dopasowanie z opóźnieniem)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`\w*?d` dopasowuje "FAD" i "Ed" w "wyblakłe", ale nie cały wyraz "wyblakł" ze względu na dopasowanie z opóźnieniem|
|Dopasowuje jedno lub więcej wystąpień poprzedniego wyrażenia (dopasowanie możliwie najmniejszej liczby znaków). Aby uzyskać więcej informacji, zobacz [dopasowanie jeden lub więcej razy (dopasowanie z opóźnieniem)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?` dopasowuje "ee" w "uśpionych" i "Ed" w "wyblakł", ale nie znajduje żadnych dopasowań w "zaniku"|
|Zakotwiczenie ciągu dopasowania do [początku wiersza lub ciągu](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car` dopasowuje słowo "samochód" tylko wtedy, gdy pojawia się na początku wiersza|
|Zakotwiczenie ciągu dopasowania do [końca wiersza](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r?$|`car\r?$` pasuje do "samochodu" tylko wtedy, gdy pojawia się na końcu wiersza|
|Zakotwiczenia ciągu dopasowania na końcu pliku|$|`car$` pasuje do "samochodu" tylko wtedy, gdy pojawia się na końcu pliku|
|Dopasuj jeden dowolny znak, które są dostępne w zestawie|[abc]|`b[abc]` pasuje do "BA", "bb" i "BC"|
|Dopasuj dowolny znak zakresu znaków|[a-f]|`be[n-t]` dopasowuje "trafienie" w "Between", "Ben" w "pod" i "BES" w "obok", ale nie znajduje żadnych pasujących elementów "poniżej"|
|Przechwytywanie i niejawne numerowanie wyrażenia zawartgoe w nawiasach|()|`([a-z])X\1` pasuje "do aXa" i "bXb", ale nie "aXb". "\1" odnosi się do pierwszej grupy wyrażenie "[a-z]". Aby uzyskać więcej informacji, zobacz [Przechwytywanie grup i wzorców zastąpień](#capture-groups-and-replacement-patterns). |
|Unieważnienie dopasowania|(?! ABC)|`real(?!ity)` pasuje do członu "real" w słowach "realty" i "really", ale nie w "reality". W "realityreal" danych znajdzie także drugi "prawdziwy" (ale nie pierwszy "prawdziwy").|
|Dopasowuje dowolny znak, który nie znajduje się w danym zestawie znaków. Aby uzyskać więcej informacji, zobacz [Grupa znaków negatywnych](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^ abc]|`be[^n-t]` dopasowuje "BEF" w "Before", "BEH" w "za" i "etykiety" w "poniżej", ale nie znajduje żadnych dopasowań w "poniżej"|
|Dopasowuje wyrażenie przed lub po symbolu|&#124;|`(sponge|mud) bath` pasuje do "kąpieli gąbki" i "kąpiel Mud"|
|[Znak ucieczki](/dotnet/standard/base-types/character-escapes-in-regular-expressions) po ukośniku odwrotnym| \\ |`\^` dopasowuje znak ^|
|Określ liczbę wystąpień poprzedzającego znaku lub grupy. Aby uzyskać więcej informacji, zobacz [dopasowanie dokładnie n razy](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, gdzie "n" jest liczbą wystąpień|`x(ab){2}x` pasuje do "xababx"<br/>`x(ab){2,3}x` pasuje do "xababx" i "xabababx", ale nie "xababababx"|
|[Dopasowuje tekst w kategorii Unicode](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Aby uzyskać więcej informacji na temat klas znaków Unicode, zobacz [Unicode Standard 5,2 Properties](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, gdzie "X" jest numerem kodu Unicode.|`\p{Lu}` dopasowuje "T" i "D" w "Thomas Nowak"|
|[Dopasowuje granicę słowa](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (poza klasą znak `\b` określa granicy słowa i wewnątrz znak klasy `\b` określa backspace.)|`\bin` dopasowuje "in" w "wewnątrz", ale nie znajduje żadnych dopasowań w "Pinto"|
|Dopasowuje podział wiersza (oznacza to, że znak powrotu karetki następuje po nowym wierszu)|\r?\n|`End\r?\nBegin` dopasowuje "End" i "BEGIN" tylko wtedy, gdy "koniec" jest ostatnim ciągiem w wierszu i "BEGIN" jest pierwszym ciągiem w następnym wierszu|
|Dopasowuje dowolny [znak słowa](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd` pasuje do "Add" i "A1d", ale nie do "a d"|
|Dopasowuje dowolny [znak odstępu](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface` Dopasowuje frazę "interfejs publiczny"|
|Dopasowuje dowolny [znak cyfry dziesiętnej](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d` pasuje do wartości "4" i "0" w "WD40"|

Przykładowe wyrażenie regularne, które łączy niektóre operatory i konstrukcje do dopasowania do liczby szesnastkowej, jest `\b0[xX]([0-9a-fA-F]+\)\b`. To wyrażenie pasuje do "0xc67f", ale nie "0xc67g".

> [!TIP]
> W systemach operacyjnych Windows większość linii kończyć się "\r\n" (znak powrotu karetki następuje nowy wiersz). Te znaki nie są widoczne, ale są obecne w edytorze i przechodzą do usługi wyrażeń regularnych programu .NET.

## <a name="capture-groups-and-replacement-patterns"></a>Przechwyć grupy i wzorce zastępujące

Grupa przechwytywania wyznacza Podwyrażenie wyrażenia regularnego i przechwytuje podciąg ciągu wejściowego. Przechwyconych grup można użyć w wyrażeniu regularnym (na przykład w celu wyszukania Powtórzonego słowa) lub w wzorcu zastępczym. Aby uzyskać szczegółowe informacje, zobacz [grupowanie konstrukcji w wyrażeniach regularnych](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Aby utworzyć numerowaną grupę przechwytywania, umieść Podwyrażenie z nawiasami we wzorcu wyrażenia regularnego. Przechwytywanie są numerowane automatycznie od lewej do prawej w oparciu o pozycję nawiasu otwierającego w wyrażeniu regularnym. Aby uzyskać dostęp do przechwyconej grupy:

- **w wyrażeniu regularnym**: Użyj `\number`. Na przykład `\1` w wyrażeniu regularnym `(\w+)\s\1` odwołuje się do pierwszej grupy przechwytywania `(\w+)`.

- **w wzorcu wymiany**: Użyj `$number`. Na przykład grupowanych wyrażenia regularnego `(\d)([a-z])` definiuje dwie grupy: pierwsza grupa zawiera pojedynczą cyfrą dziesiętną, a drugiej grupy pojedynczy znak między **a** i **z**. Wyrażenie umożliwia znalezienie dopasowania cztery następujący ciąg: **1a 2b 3c 4d**. Ciąg zamienny `z$1` odwołuje się tylko do pierwszej grupy (`$1`) i konwertuje ciąg na **Z1 Z2 Z3 Z4**.

Na poniższej ilustracji przedstawiono `(\w+)\s\1` wyrażenia regularnego i zastępczy ciąg `$1`. Zarówno wyrażenie regularne, jak i wzorzec zastępczy odwołują się do pierwszej grupy przechwytywania, która jest automatycznie numerowana 1. Po wybraniu opcji **Zamień wszystkie** w oknie dialogowym **szybkie zamienianie** w programie Visual Studio powtórzone słowa są usuwane z tekstu.

![Szybkie zastępowanie przedstawiające numerowaną grupę przechwytywania w programie Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Upewnij się, że w oknie dialogowym **szybkie zamienianie** jest zaznaczone pole wyboru **Użyj wyrażeń regularnych** .

### <a name="named-capture-groups"></a>Nazwane grupy przechwytywania

Zamiast polegać na automatycznym numerowaniu grupy przechwytywania, można nadać jej nazwę. Składnia nazwanej grupy przechwytywania jest `(?<name>subexpression)`.

Nazwane grupy przechwytywania, takie jak numerowane grupy przechwytywania, mogą być używane wewnątrz wyrażenia regularnego lub w wzorcu zamiennym. Aby uzyskać dostęp do nazwanej grupy przechwytywania:

- **w wyrażeniu regularnym**: Użyj `\k<name>`. Na przykład `\k<repeated>` w wyrażeniu regularnym `(?<repeated>\w+)\s\k<repeated>` odwołuje się do grupy przechwytywania o nazwie `repeated` i której Podwyrażenie jest `\w+`.

- **w wzorcu wymiany**: Użyj `${name}`. Na przykład `${repeated}`.

Na przykład na poniższym obrazie przedstawiono wyrażenie regularne `(?<repeated>\w+)\s\k<repeated>` i ciąg zastępczy `${repeated}`. Zarówno wyrażenie regularne, jak i zastępczy wzorzec odwołują się do grupy przechwytywania o nazwie `repeated`. Po wybraniu opcji **Zamień wszystkie** w oknie dialogowym **szybkie zamienianie** w programie Visual Studio powtórzone słowa są usuwane z tekstu.

![Szybkie zastępowanie przedstawiające nazwaną grupę przechwytywania w programie Visual Studio](media/named-capture-group.png)

> [!TIP]
> Upewnij się, że w oknie dialogowym **szybkie zamienianie** jest zaznaczone pole wyboru **Użyj wyrażeń regularnych** .

Aby uzyskać więcej informacji na temat nazwanych grup przechwytywania, zobacz [nazwane Podwyrażenie dopasowane](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Aby uzyskać więcej informacji na temat wyrażeń regularnych, które są używane w wzorcach zamiennych, zobacz [podstawienia w wyrażeniach regularnych](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
