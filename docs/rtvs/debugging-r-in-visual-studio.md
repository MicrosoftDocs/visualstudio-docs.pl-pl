---
title: Debugowanie kodu R
description: Program Visual Studio oferuje pełne środowisko debugowania dla języka R, w tym punkty przerwania, dołączania, stosu wywołań i inspekcji zmiennych.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: e3696cac00c726cffb76f29a1da2c503a15af2bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885823"
---
# <a name="debug-r-in-visual-studio"></a>Debugowanie języka R w programie Visual Studio

R Tools for Visual Studio (RTVS) integruje się z pełnym interfejsem debugowania programu Visual Studio (zobacz [debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md). Ta obsługa obejmuje punkty przerwania, dołączanie do uruchomionych procesów, sprawdzanie i oglądanie zmiennych oraz sprawdzanie stosu wywołań. W tym artykule omówiono te aspekty debugowania, które są unikatowe dla języka R i RTVS.

Uruchamianie debugera dla pliku r Start w projekcie języka r jest takie samo jak w przypadku innych typów projektów: Użyj **debugowania**  >  **Rozpocznij debugowanie**, klawisz **F5** lub **źródłowego pliku startowego** na pasku narzędzi debugowania:

![Przycisk startowy debugera dla języka R](media/debugger-start-button.png)

Aby zmienić plik startowy, kliknij prawym przyciskiem myszy plik w Eksplorator rozwiązań i wybierz polecenie **Ustaw jako startowy skrypt języka R**.

We wszystkich przypadkach uruchomienie debugera "źródła" pliku w oknie interaktywnym, co oznacza załadowanie go i uruchomienie go w sposób pokazany w danych wyjściowych okna interaktywnego:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Zauważ, że `rtvs::debug_source` Funkcja jest używana do źródła skryptu. Ta funkcja jest wymagana, ponieważ RTVS musi zmodyfikować kod w przygotowaniu do debugowania. W przypadku korzystania z dowolnego polecenia RTVS pozyskania i dołączenia debugera program Visual Studio automatycznie używa `rtvs::debug_source` .

Można również ręcznie dołączyć debuger z okna interaktywnego bezpośrednio za pomocą polecenia programu **R Tools**  >    >  **Attach Debugger** , polecenia **Debug**  >  **Attach to R Interactive** lub **Dołącz debuger** na pasku narzędzi okna interaktywnego. Po wykonaniu tej czynności użytkownik jest odpowiedzialny za źródło plików, które mają być debugowane. Jeśli chcesz ręcznie tworzyć pliki źródłowe, upewnij się, że używasz, `rtvs::debug_source` a nie zwykłego `source` polecenia w języku R.

To połączenie między debugerem a oknem interaktywnym ułatwia wykonywanie takich czynności, jak wywoływanie funkcji (i debugowanie) przy użyciu różnych wartości parametrów. Załóżmy na przykład, że masz następującą funkcję w pliku źródłowym (oznacza to, że został on załadowany do sesji):

```R
add <- function(x, y) {
    return(x + y)
}
```

Następnie ustaw punkt przerwania na `return` instrukcji. Teraz, w oknie interaktywnym, wprowadzanie powoduje `add(4,5)` zatrzymanie debugera w punkcie przerwania.

## <a name="environment-browser-in-the-interactive-window"></a>Przeglądarka środowiska w oknie interaktywnym

Po zatrzymaniu w debugerze, w [oknie interaktywnym](interactive-repl-for-r-in-visual-studio.md)zostanie również zatrzymana w wierszu przeglądarki środowiska. Monit pojawia się, `Browse[n]>` gdzie n jest liczbą.

Przeglądarka środowiskowa obsługuje kilka specjalnych poleceń:

| Polecenie | Opis |
| --- | --- |
| n | Następny: uruchamia następną instrukcję w pliku kodu (taką samą jak krok powyżej). |
| s | Wkrocz do: uruchamia następną instrukcję w pliku kodu, przechodzenie do zakresu funkcji, jeśli Następna instrukcja jest wywołaniem funkcji. |
| f | zakończenie: powoduje uruchomienie pozostałej części bieżącego zakresu funkcji i powrót do obiektu wywołującego (tak samo jak krok wychodzący). |
| c, kontynuacja | Kontynuuj: uruchamia program do następnego punktu przerwania. |
| Q | zakończenia: kończy sesję debugowania. |
| gdzie | Pokaż stos: wyświetla stos wywołań w oknie interaktywnym. |
| Pomoc | Pokaż Pomoc: wyświetla dostępne polecenia w oknie interaktywnym. |
| &lt;wyrażenie&gt; | Oblicz wyrażenie w wyrażeniu *.* |

![Przeglądarka środowiska w oknie interaktywnym](media/debugger-environment-browser.png)
