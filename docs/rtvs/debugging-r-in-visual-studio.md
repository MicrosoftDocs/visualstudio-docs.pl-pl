---
title: Debugowanie kodu języka R
description: Program Visual Studio udostępnia pełnego środowiska debugowania dla języka R, w tym punkty przerwania, dołączanie, wywołaniach stosów i sprawdzanie zmiennych.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: da72f68d72a435ebf7fe90a7a7d5b6141e409f07
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918371"
---
# <a name="debug-r-in-visual-studio"></a>Debugowanie języka R w programie Visual Studio

Narzędzia R Tools for Visual Studio (RTVS) integruje się z pełnego środowiska debugowania programu Visual Studio (zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugger-feature-tour). Ta obsługa obejmuje punkty przerwania, dołączanie do uruchomionego procesu, kontroli i oglądaniu zmiennych i sprawdzanie stosu wywołań. W tym artykule przedstawiono następnie aspekty debugowania, które są unikatowe dla języków R i RTVS.

Uruchamianie debugera, aby plik startowy języka R, w projekcie języka R jest taka sama, jak w przypadku innych typów projektów: Użyj **debugowania** > **Rozpocznij debugowanie**, **F5** klucza, lub **Źródłowy plik startowy** na pasku narzędzi debugowania:

![Przycisk Uruchom debuger dla języka R](media/debugger-start-button.png)

Aby zmienić plik startowy, kliknij prawym przyciskiem myszy plik w Eksploratorze rozwiązań i wybierz **ustawiona jako uruchamiania skryptu języka R**.

We wszystkich przypadkach uruchamianie debugera "źródła" w pliku w oknie interaktywnym, co oznacza załadowanie go i uruchomiania go tam, jak pokazano w danych wyjściowych w oknie interaktywnym:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Należy zauważyć, że `rtvs::debug_source` funkcja jest używana do źródła skryptu. Ta funkcja jest wymagana, ponieważ RTVS trzeba zmodyfikować kod w ramach przygotowania do debugowania. Jeśli przy użyciu dowolnego polecenia pozyskania RTVS i Debuger jest dołączony, program Visual Studio automatycznie używa `rtvs::debug_source`.

Można też ręcznie dołączyć debuger, w oknie interaktywnym bezpośrednio przy użyciu **R Tools** > **sesji** > **dołączyć debuger** polecenie **debugowania** > **dołączyć do interaktywne R** polecenia lub **dołączyć debuger** polecenia na pasku narzędzi w oknie interaktywnym. Po wykonaniu czynności jest odpowiedzialny za pliki źródłowe, które chcesz debugować. Jeśli chcesz ręcznie pliki źródłowe, upewnij się, że używasz `rtvs::debug_source` i nie zwykłych `source` polecenia w języku R.

To połączenie między debugera i oknie interaktywnym ułatwia wykonywanie takich czynności jak wywołania (i debugowanie) funkcja z wartościami różnych parametrów. Na przykład załóżmy, że masz następującej funkcji w pliku pochodzenia (znaczenie, gdy jest on ładowany do sesji):

```R
add <- function(x, y) {
    return(x + y)
}
```

Następnie ustaw punkt przerwania na `return` instrukcji. W oknie interaktywnym, wprowadzając `add(4,5)` powoduje zatrzymanie debugera na punkt przerwania.

## <a name="environment-browser-in-the-interactive-window"></a>Przeglądarka środowiska w oknie interaktywnym

Podczas zatrzymywania jest debugera, również one został zatrzymany w wierszu przeglądarka środowiska [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md). Monit jest wyświetlany jako `Browse[n]>` gdzie n to liczba.

Przeglądarka środowisko obsługuje wiele poleceń specjalne:

| Polecenie | Opis |
| --- | --- |
| n | Następny: uruchomienia następnej instrukcji w kodzie pliku (tak samo jak Przekrocz). |
| s | Wkrocz do: uruchamia następną instrukcję w pliku kodu, przechodzenie do zakresu funkcji, jeśli następna instrukcja jest wywołaniem funkcji. |
| f | Zakończenie: jest uruchamiany w pozostałej części bieżącego zakresu funkcji i do obiektu wywołującego (tak samo, jak krok out). |
| c, CD | Kontynuuj: uruchamia program do następnego punktu przerwania. |
| Q | kończy działanie: kończy sesję debugowania. |
| gdzie | Pokaż stos: zawiera stos wywołań w oknie interaktywnym. |
| Pomoc | Pokaż Pomoc: Wyświetla dostępne polecenia w oknie interaktywnym. |
| &lt;expr&gt; | obliczenie wyrażenia w *expr*. |

![Przeglądarka środowiska w oknie interaktywnym](media/debugger-environment-browser.png)
