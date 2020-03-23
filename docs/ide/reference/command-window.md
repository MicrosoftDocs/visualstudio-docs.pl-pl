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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570352"
---
# <a name="command-window"></a>Okno polecenia
Okno **Command** służy do wykonywania poleceń lub aliasów bezpośrednio w zintegrowanym [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisku programistycznym (IDE). Można wykonać zarówno polecenia menu, jak i polecenia, które nie są wyświetlane w żadnym menu. Aby wyświetlić okno **Polecenia,** wybierz polecenie **Inne okna** z menu **Widok** i wybierz polecenie **Okno polecenia**.

## <a name="displaying-the-values-of-variables"></a>Wyświetlanie wartości zmiennych
Aby sprawdzić wartość zmiennej, `varA`użyj polecenia [Drukuj:](../../ide/reference/print-command.md)

```cmd
>Debug.Print varA
```

Znak zapytania (?) jest aliasem dla `Debug.Print`, więc to polecenie może być również napisane:

```cmd
>? varA
```

Obie wersje tego polecenia zwróci wartość `varA`zmiennej .

## <a name="entering-commands"></a>Wprowadzanie poleceń
Większy niż symbol`>`( ) pojawia się na lewej krawędzi okna Polecenia jako monit dla nowych wierszy. Użyj klawiszy STRZAŁKA W GÓRĘ i STRZAŁKA W DÓŁ, aby przewijać wcześniej wydane polecenia.

|Zadanie|Rozwiązanie|Przykład|
|----------|--------------|-------------|
|Oceń wyrażenie.|Przedmową wyrażenie znakiem zapytania`?`( ).|`? myvar`|
|Przełącz się do okna natychmiastowego.|Wprowadź `immed` do okna bez znaku większego niż (>)|`immed`|
|Przełącz się z powrotem do okna polecenia z okna natychmiastowego.|Wprowadź `cmd` do okna.|`>cmd`|

Poniższe skróty ułatwią nawigację w trybie polecenia.

|Akcja|Lokalizacja kursora|Keybinding|
|------------| - |----------------|
|Przechodzenie między poprzednimi poleceniami.|Linia wejściowa|STRZAŁKA W GÓRĘ & STRZAŁKA W DÓŁ|
|Przewiń okno w górę.|Zawartość okna polecenia|CTRL + STRZAŁKA W GÓRĘ|
|Przewiń w dół okna.|Zawartość okna polecenia|STRZAŁKA W DÓŁ lub CTRL+STRZAŁKA W DÓŁ|

> [!TIP]
> Całe poprzednie polecenie lub jego część można skopiować do wiersza wejściowego, przewijając do niego, zaznaczając całość lub część, a następnie naciskając klawisz ENTER.

## <a name="mark-mode"></a>Tryb oznaczania
Po kliknięciu dowolnego poprzedniego wiersza w oknie **Polecenia** automatycznie przełączasz się w tryb oznaczania. Umożliwia to zaznaczanie, edytowanie i kopiowanie tekstu poprzednich poleceń, tak jak w dowolnym edytorze tekstu, i wklejania ich do bieżącego wiersza.

## <a name="the-equals--sign"></a>Znak równy (=)
Okno używane do `EvaluateStatement` wprowadzenia polecenia określa, czy znak równości (=) jest interpretowany jako operator porównania, czy jako operator przypisania.

W oknie **Command** znak równości (=) jest interpretowany jako operator porównania. Operatory przypisań nie mogą być używane w oknie **Polecenia.** Tak więc, na przykład, jeśli `varA` `varB` wartości zmiennych i `>Debug.EvaluateStatement(varA=varB)` są różne, `False`polecenie zwróci wartość .

Natomiast w oknie **Natychmiastowy** znak równy (=) jest interpretowany jako operator przypisania. Tak więc, na `>Debug.EvaluateStatement(varA=varB)` przykład, polecenie `varA` przypisze `varB`do zmiennej wartość zmiennej .

## <a name="parameters-switches-and-values"></a>Parametry, przełączniki i wartości
Niektóre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] polecenia mają wymagane i opcjonalne argumenty, przełączniki i wartości. Niektóre zasady mają zastosowanie w przypadku takich poleceń. Poniżej przedstawiono przykład polecenia rich, aby wyjaśnić terminologię.

```cmd
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

W tym przykładzie

- `Edit.ReplaceInFiles`jest poleceniem

- `/case`i `/pattern:regex` są przełącznikami (poprzedzonymi znakiem ukośnika [/])

- `regex`jest wartością `/pattern` przełącznika; przełącznik `/case` nie ma wartości

- `var[1-3]+`i `oldpar` są parametrami

    > [!NOTE]
    > Każde polecenie, parametr, przełącznik lub wartość zawierająca spacje muszą mieć podwójne cudzysłowy po obu stronach.

Położenie przełączników i parametrów można swobodnie wymieniać w wierszu polecenia, z wyjątkiem polecenia [Shell,](../../ide/reference/shell-command.md) które wymaga jego przełączników i parametrów w określonej kolejności.

Prawie każdy przełącznik obsługiwany przez polecenie ma dwie formy: krótki (jeden znak) i długą formę. Wiele przełączników krótkich formularzy można łączyć w grupę. Na przykład, `/p /g /m` mogą być wyrażone na przemian jako `/pgm`.

Jeśli przełączniki krótkiego kształtu są łączone w grupę i otrzymują wartość, wartość ta ma zastosowanie do każdego przełącznika. Na przykład `/pgm:123` równa `/p:123 /g:123 /m:123`się . Błąd występuje, jeśli którykolwiek z przełączników w grupie nie akceptuje wartości.

## <a name="escape-characters"></a>Znaki ucieczki
Znak cieszy (^) w wierszu polecenia oznacza, że znak bezpośrednio po nim jest interpretowany dosłownie, a nie jako znak kontrolny. Może to służyć do osadzania prostych cudzysłowów ("), spacji, ukośników wiodących, pasków dołek lub innych znaków literału w wartości parametru lub przełącznika, z wyjątkiem nazw przełączników. Na przykład:

```cmd
>Edit.Find ^^t /regex
```

Czyn y pielęgnacyjny działa tak samo, niezależnie od tego, czy znajduje się wewnątrz, czy poza cudzysłowami. Jeśli ciesza jest ostatnim znakiem w wierszu, jest ignorowana. W przykładzie pokazanym w tym miejscu pokazano, jak wyszukać wzorzec "^t".

## <a name="use-quotes-for-path-names-with-spaces"></a>Używanie cudzysłowów dla nazw ścieżek ze spacjami
Jeśli na przykład chcesz otworzyć plik zawierający ścieżkę zawierającą spacje, należy umieścić podwójne cudzysłowy wokół segmentu ścieżki lub ścieżki zawierającego spacje: **C:\\"Pliki programu"** lub **"Pliki programu".**

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
