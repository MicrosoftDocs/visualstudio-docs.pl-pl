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
ms.openlocfilehash: 5fc2e1afa95c56dda79296a24f027fb93d62c585
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747737"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Używanie wyrażeń regularnych w programie Visual Studio

Program Visual Studio używa [wyrażeń regularnych programu .NET](/dotnet/standard/base-types/regular-expressions) do znajdowania i zamieniania tekstu.

## <a name="replacement-patterns"></a>Wzorce zamieniania

Aby użyć grupy numerowanych przechwytywania, należy ująć grupy za pomocą nawiasów we wzorcu wyrażenia regularnego. Użyj `$number`, gdzie `number` jest liczbą całkowitą, zaczynając od 1, aby określić grupę określonego, numerowana we wzorcu zamieniania. Na przykład grupowanych wyrażenia regularnego `(\d)([a-z])` definiuje dwie grupy: pierwsza grupa zawiera pojedynczą cyfrą dziesiętną, a drugiej grupy pojedynczy znak między **a** i **z**. Wyrażenie wyszukuje cztery dopasowań w następujący ciąg: **1a 2b 3c 4d**. Ciąg zastępujący `z$1` odwołuje się do pierwszej grupy, a następnie konwertuje ciąg na **z1 z2 z3 z4**.

Aby uzyskać informacje o wyrażeniach regularnych, które są używane we wzorcach zamieniania, zobacz [podstawienia w wyrażeniach regularnych (Przewodnik platformy .NET)](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="regular-expression-examples"></a>Przykłady wyrażeń regularnych

Oto kilka przykładów:

|Cel|Wyrażenie|Przykład|
|-------------|----------------|-------------|
|Dopasuj jeden dowolny znak (oprócz podziału wiersza)|.|`a.o` pasuje "aro" w "around" i "abo" w "about" ale nie "acro" w "w".|
|Dopasowuje zero lub więcej wystąpień poprzedniego wyrażenia (dopasowuje tak dużą liczbę znaków, jak to możliwe)|*|`a*r` pasuje "r" w "rack", "ar" w "ark" i "aar" w "aardvark"|
|Dopasowuje dowolny znak zero lub więcej razy (symbol wieloznaczny *)|.*|`c.*e` pasuje do "cke" w "racket", "comme" w "comment" i "code" w "code"|
|Pasuje jedno lub więcej wystąpień poprzedniego wyrażenia (dopasowuje tak dużą liczbę znaków, jak to możliwe)|+|`e.+d` pasuje do "eed" w "feeder" ale nie "ed".|
|Dopasowuje dowolny znak jeden lub więcej razy (symbol wieloznaczny?)|.+|`e.+e` pasuje do "eede" w "feeder" ale nie "ee".|
|Dopasowuje zero lub więcej wystąpień poprzedniego wyrażenia (dopasowuje tak małą znaków, jak to możliwe)|*?|`e.*?e` pasuje do "ee" w "feeder" ale nie do "eede".|
|Pasuje jedno lub więcej wystąpień poprzedniego wyrażenia (dopasowuje tak małą znaków, jak to możliwe)|+?|`e.+?e` pasuje "do ente" i "erprise" w "enterprise", ale nie całego słowa "enterprise".|
|Zakotwiczenia ciągu dopasowania do początku wiersza lub ciągu|^|`^car` Dopasowuje słowa "samochód" tylko wtedy, gdy pojawia się na początku wiersza.|
|Zakotwiczenia ciągu dopasowania na końcu wiersza|\r?$|`end\r?$` pasuje do "end" tylko wtedy, gdy pojawia się na końcu wiersza.|
|Zakotwiczenia ciągu dopasowania na końcu pliku|$|`end$` pasuje do "end" tylko wtedy, gdy pojawia się na końcu pliku.|
|Dopasuj jeden dowolny znak, które są dostępne w zestawie|[abc]|`b[abc]` pasuje do "ba", "bb" i "bc".|
|Dopasuj dowolny znak zakresu znaków|[a-f]|`be[n-t]` Dopasowuje "bet" w "between", "ben" w "beneath" i "bes" w "beside", ale nie "below".|
|Przechwytywanie i niejawne numerowanie wyrażenia zawartgoe w nawiasach|()|`([a-z])X\1` pasuje "do aXa" i "bXb", ale nie "aXb". "\1" odnosi się do pierwszej grupy wyrażenie "[a-z]".|
|Unieważnienie dopasowania|(?! ABC)|`real(?!ity)` pasuje do członu "real" w słowach "realty" i "really", ale nie w "reality". W "realityreal" danych znajdzie także drugi "prawdziwy" (ale nie pierwszy "prawdziwy").|
|Dopasowuje dowolny znak, który nie znajduje się w danym zestawie znaków|[^ abc]|`be[^n-t]` pasuje "do bef" w "przed", "beh" w "za" i "bel" w "below", ale nie "beneath".|
|Dopasowuje wyrażenie przed lub po symbolu.|&#124;|`(sponge\|mud) bath` pasuje "sponge bath" i "mud bath."|
|Uniknij znaku następującej odwróconej kreski ukośnej| \\ |`\^` pasuje do znaku ^.|
|Określ liczbę wystąpień poprzedzającego znaku lub grupy|{x},, gdzie x jest liczbą wystąpień|`x(ab){2}x` odpowiada "xababx" i `x(ab){2,3}x` odpowiada "xababx" i "xabababx", ale nie "xababababx".|
|Dopasowuje tekst w klasie znaku Unicode. Aby uzyskać więcej informacji dotyczących klas znaków Unicode zobacz<br /><br /> [Właściwości znaków standardu Unicode 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, gdzie "X" jest numerem kodu Unicode.|`\p{Lu}` pasuje do "T" i "D" w "Thomas Doe".|
|Dopasuj granicę wyrazu|\b (poza klasą znak `\b` określa granicy słowa i wewnątrz znak klasy `\b` określa backspace.)|`\bin` pasuje do "w" w "wewnątrz" ale nie "pinto".|
|Dopasowuje znak końca wiersza (czyli znak powrotu karetki następuje nowy wiersz).|\r?\n|`End\r?\nBegin` pasuje do "Koniec" i "Początek" tylko wtedy, gdy "Koniec" jest ostatnim ciągiem w wierszu a "Początek" jest pierwszym ciągiem w następnym wierszu.|
|Pasuje do dowolnego znaku alfanumerycznego|\w|`a\wd` Dopasowuje "add" i "a1d" ale nie "d".|
|Dopasowuje dowolny biały znak.|\s|`Public\sInterface` pasuje do frazy "Interfejs publiczny".|
|Dopasuj dowolną cyfrę|\d|`\d` pasuje i "3" w "3456", "2" w 23" i"1"w"1".|
|Dopasowuje znak Unicode|\uXXXX gdzie XXXX określa wartość znaku Unicode.|`\u0065` Dopasowuje znak "e".|
|Dopasuj identyfikator|\b [\_\w-[0-9]] [\_\w]*\b|Dopasowuje "type1", ale nie "& type1" lub "#define".|
|Dopasuj ciąg w cudzysłowie|((\\".+?\\")&#124;('.+?'))|Dopasowuje dowolny ciąg w pojedynczym lub podwójnym cudzysłowie.|
|Dopasuj liczbę szesnastkową|\b0[xX]([0-9a-fA-F]+\)\b|Dopasowuje "0xc67f", ale nie "0xc67g".|
|Dopasuj liczby całkowite i miejsca dziesiętne|\b[0-9]*\\.\*[0-9]+\b|Dopasowuje "1,333".|

> [!TIP]
> W systemach operacyjnych Windows większość linii kończyć się "\r\n" (znak powrotu karetki następuje nowy wiersz). Te znaki nie są widoczne, ale są obecne w edytorze i są przekazywane do usługi wyrażenie regularne .NET.

## <a name="see-also"></a>Zobacz także

- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
