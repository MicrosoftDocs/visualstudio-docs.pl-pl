---
title: Debugowanie kodu R
description: Visual Studio zapewnia pełne środowisko debugowania dla języka R, w tym punkty przerwania, dołączyć, stos wywołań i inspekcji zmiennych.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 5efa0a32f51e1f5060474a0d277bfca7f1e7d548
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189259"
---
# <a name="debug-r-in-visual-studio"></a>Debug R w programie Visual Studio

Narzędzia R dla programu Visual Studio (RTVS) integrują się z pełnym działaniem debugowania programu Visual Studio (zobacz [Debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md). Ta obsługa obejmuje punkty przerwania, dołączanie do uruchomionych procesów, sprawdzanie i obserwowanie zmiennych oraz sprawdzanie stosu wywołań. W tym artykule, a następnie eksploruje te aspekty debugowania, które są unikatowe dla R i RTVS.

Uruchamianie debugera dla uruchamiania pliku R w projekcie R jest takie samo jak w przypadku innych typów projektów: użyj **debugowania** > **startowego debugowania, klucza** **F5** lub **pliku uruchamiania źródła** na pasku narzędzi debugowania:

![Przycisk start debugera dla R](media/debugger-start-button.png)

Aby zmienić plik startowy, kliknij prawym przyciskiem myszy plik w Eksploratorze rozwiązań i wybierz polecenie **Ustaw jako skrypt R uruchamiania**.

We wszystkich przypadkach, uruchomienie debugera "źródła" pliku w oknie interaktywnym, co oznacza ładowanie go i uruchamianie go tam, jak pokazano w interaktywnym oknie danych wyjściowych:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Należy zauważyć, że `rtvs::debug_source` funkcja jest używana do źródła skryptu. Ta funkcja jest wymagana, ponieważ RTVS musi zmodyfikować kod w ramach przygotowań do debugowania. W przypadku korzystania z dowolnego polecenia zaopatrzenia RTVS i dołączonego `rtvs::debug_source`debugera program Visual Studio automatycznie używa .

Debugera z okna interaktywnego można również dołączyć ręcznie, korzystając z polecenia**Debuger** **dołączania** >  **sesji** > R, polecenia **Debugowanie** > **Dołącz do języka R interactive** lub polecenia Dołącz **debuger** na pasku narzędzi okna interaktywnego. Po wykonaniu tej tej sprawy jest twoim obowiązkiem do źródła plików, które chcesz debugować. Jeśli chcesz ręcznie pozyskać pliki, upewnij się, że `rtvs::debug_source` `source` używasz, a nie regularne polecenie w języku R.

To połączenie między debugerem a interakcyjnym oknem ułatwia działanie takie czynności, jak wywoływanie (i debugowanie) funkcji z różnymi wartościami parametrów. Załóżmy na przykład, że w pliku źródłowym znajduje się następująca funkcja (co oznacza, że została ona załadowana do sesji):

```R
add <- function(x, y) {
    return(x + y)
}
```

Następnie należy ustawić punkt `return` przerwania na instrukcji. Teraz w oknie interaktywnym `add(4,5)` wprowadzanie zatrzymuje debugera w punkcie przerwania.

## <a name="environment-browser-in-the-interactive-window"></a>Przeglądarka środowiska w oknie interaktywnym

Po zatrzymaniu w debugerze zostanie również zatrzymany w wierszu przeglądarki środowiska w [oknie interaktywnym](interactive-repl-for-r-in-visual-studio.md). Monit jest `Browse[n]>` wyświetlany w miejscu, w którym n jest liczbą.

Przeglądarka środowiska obsługuje szereg specjalnych poleceń:

| Polecenie | Opis |
| --- | --- |
| n | dalej: uruchamia następną instrukcję w pliku kodu (tak samo jak krok po kroku). |
| s | krok do: uruchamia następną instrukcję w pliku kodu, krok po kroku do zakresu funkcji, jeśli następna instrukcja jest wywołaniem funkcji. |
| k | finish: uruchamia pozostałą część bieżącego zakresu funkcji i zwraca do wywołującego (tak samo jak wyjść). |
| c, cont | kontynuować: uruchamia program do następnego punktu przerwania. |
| Q | kończy: kończy sesję debugowania. |
| where | pokaż stos: wyświetla stos wywołań w oknie interaktywnym. |
| Pomoc | pokaż pomoc: wyświetla dostępne polecenia w oknie interaktywnym. |
| &lt;Expr&gt; | oceny wyrażenia w *expr*. |

![Przeglądarka środowiska w oknie interaktywnym](media/debugger-environment-browser.png)
