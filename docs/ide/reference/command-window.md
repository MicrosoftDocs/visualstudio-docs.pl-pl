---
title: Okno polecenia
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb855cbed67bffc5ff2fb63b1785c577dd9fea25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75570352"
---
# <a name="command-window"></a>Okno polecenia
Okno **polecenia** służy do wykonywania poleceń lub aliasów bezpośrednio w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku programistycznym (IDE). Można wykonać Oba polecenia menu i polecenia, które nie są wyświetlane w żadnym menu. Aby wyświetlić okno **poleceń** , wybierz **inne okna** z menu **Widok** i wybierz **polecenie Okno**.

## <a name="displaying-the-values-of-variables"></a>Wyświetlanie wartości zmiennych
Aby sprawdzić wartość zmiennej `varA` , użyj [polecenia Print](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

Znak zapytania (?) jest aliasem dla `Debug.Print` , więc można także napisać to polecenie:

```cmd
>? varA
```

Obie wersje tego polecenia zwróci wartość zmiennej `varA` .

## <a name="entering-commands"></a>Wprowadzanie poleceń
Symbol większe niż ( `>` ) pojawia się na lewej krawędzi okno polecenie jako monit dla nowych wierszy. Użyj klawiszy Strzałka w górę i Strzałka w dół, aby przewijać wcześniej wystawione polecenia.

|Zadanie|Rozwiązanie|Przykład|
|----------|--------------|-------------|
|Oceń wyrażenie.|Oznacz wyrażenie znakiem zapytania ( `?` ).|`? myvar`|
|Przełącz do okna bezpośredniego.|Wprowadź `immed` do okna bez znaku większości (>)|`immed`|
|Przełącz się z powrotem do okno Polecenie z poziomu okna bezpośredniego.|Wprowadź `cmd` w oknie.|`>cmd`|

Poniższe skróty ułatwiają nawigowanie w trybie poleceń.

|Akcja|Lokalizacja kursora|Powiązanie klawiszy|
|------------| - |----------------|
|Przechodź przez listę poprzednio wprowadzonych poleceń.|Wiersz wejściowy|STRZAŁKA W GÓRĘ & STRZAŁKA W DÓŁ|
|Przewiń okno do góry.|Zawartość okno Polecenie|CTRL + STRZAŁKA W GÓRĘ|
|Przewiń okno w dół.|Zawartość okno Polecenie|Strzałka w dół lub CTRL + STRZAŁKA w dół|

> [!TIP]
> Możesz skopiować wszystko lub część poprzedniego polecenia do wiersza wejściowego, przewijając do niego, zaznaczając wszystko lub jego część, a następnie naciskając klawisz ENTER.

## <a name="mark-mode"></a>Tryb oznaczania
Po kliknięciu dowolnego poprzedniego wiersza w oknie **poleceń** zostanie ono automatycznie przesunięte do trybu oznaczania. Dzięki temu można wybrać, edytować i skopiować tekst poprzednich poleceń tak samo jak w dowolnym edytorze tekstów i wkleić je do bieżącego wiersza.

## <a name="the-equals--sign"></a>Znak równości (=)
Okno używane do wprowadzania `EvaluateStatement` polecenia określa, czy znak równości (=) jest interpretowany jako operator porównania, czy jako operator przypisania.

W oknie **polecenia** znak równości (=) jest interpretowany jako operator porównania. Nie można używać operatorów przypisania w oknie **poleceń** . Tak więc, na przykład, jeśli wartości zmiennych `varA` i `varB` są różne, polecenie `>Debug.EvaluateStatement(varA=varB)` zwróci wartość `False` .

W oknie **bezpośrednim** , z przeciwieństwem, znak równości (=) jest interpretowany jako operator przypisania. Na przykład polecenie `>Debug.EvaluateStatement(varA=varB)` przypisze do zmiennej `varA` wartość zmiennej `varB` .

## <a name="parameters-switches-and-values"></a>Parametry, przełączniki i wartości
Niektóre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] polecenia mają wymagane i opcjonalne argumenty, przełączniki i wartości. Niektóre reguły mają zastosowanie podczas pracy z takimi poleceniami. Poniżej znajduje się przykład rozbudowanego polecenia, aby wyjaśnić terminologię.

```cmd
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

W tym przykładzie

- `Edit.ReplaceInFiles` jest poleceniem

- `/case` i `/pattern:regex` są przełącznikami (poprzedzone znakiem ukośnika [/])

- `regex` jest wartością `/pattern` przełącznika; `/case` przełącznik nie ma wartości

- `var[1-3]+` i `oldpar` są parametrami

    > [!NOTE]
    > Każde polecenie, parametr, przełącznik lub wartość zawierająca spacje muszą mieć podwójne cudzysłowy po obu stronach.

Położenie przełączników i parametrów można swobodnie zmieniać w wierszu polecenia z wyjątkiem polecenia [powłoki](../../ide/reference/shell-command.md) , które wymaga jego przełączników i parametrów w określonej kolejności.

Niemal każdy przełącznik obsługiwany przez polecenie ma dwie formy: krótką (jednoznakową) formę i długą formę. Do grupy można łączyć wiele przełączników skróconych. Na przykład `/p /g /m` można wyrazić alternatywę jako `/pgm` .

Jeśli przełączniki krótkie są łączone w grupę i mają daną wartość, ta wartość ma zastosowanie do każdego przełącznika. Na przykład jest `/pgm:123` równe `/p:123 /g:123 /m:123` . Błąd występuje, jeśli którykolwiek z przełączników w grupie nie akceptuje wartości.

## <a name="escape-characters"></a>Znaki ucieczki
Znak daszka (^) w wierszu polecenia oznacza, że znak bezpośrednio po nim jest interpretowany dosłownie, a nie jako znak kontrolny. Można go użyć do osadzenia prostych cudzysłowów ("), spacji, ukośników wiodących, karetki lub innych znaków literału w wartości parametru lub przełącznika, z wyjątkiem nazw przełączników. Przykład:

```cmd
>Edit.Find ^^t /regex
```

Daszek działa tak samo, niezależnie od tego, czy znajduje się wewnątrz, czy poza cudzysłowem. Jeśli karetka jest ostatnim znakiem w wierszu, zostanie zignorowana. W poniższym przykładzie pokazano, jak wyszukać wzorzec "^ t".

## <a name="use-quotes-for-path-names-with-spaces"></a>Używanie cudzysłowów dla nazw ścieżek ze spacjami
Jeśli na przykład chcesz otworzyć plik, który ma ścieżkę zawierającą spacje, musisz umieścić podwójne cudzysłowy wokół segmentu ścieżki lub ścieżki zawierającej spacje: **C: \\ "Program Files"** lub **"C:\Program Files"**.

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
