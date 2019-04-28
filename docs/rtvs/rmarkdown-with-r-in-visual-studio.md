---
title: Znaczniki R Markdown
description: Jak utworzyć dokumenty R Markdown w programie Visual Studio do tworzenia wysokiej jakości raporty, prezentacje i pulpitów nawigacyjnych.
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: b8f87f831c8076b22a61d7032d16be8d13f21b62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998648"
---
# <a name="create-r-markdown-documents"></a>Tworzenie dokumentów R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) jest formatem dokumentu, który jest przekształcany analizy w języku R wysokiej jakości dokumenty, raporty, prezentacje i pulpitów nawigacyjnych.

Narzędzia R Tools for Visual Studio (RTVS) zawiera szablon elementu R Markdown, Edytor obsługuje (w tym funkcji IntelliSense dla kodu języka R w edytorze), możliwości generowania plików i Podgląd na żywo.

## <a name="using-r-markdown"></a>Przy użyciu języka R Markdown

1. Zamknij program Visual Studio.
1. (Tylko raz) Zainstaluj `pandoc` z [pandoc.org](http://pandoc.org/installing.html).
1. Uruchom ponownie Visual Studio, które powinny przejmą instalacji pandoc.
1. Zainstaluj `knitr` i `rmarkdown` pakietów, które można zrobić z [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. Utwórz nowy plik R Markdown, przy użyciu **pliku** > **New** > **pliku** polecenia menu i wybierając polecenie **R**  >  **R Markdown** z listy. W kontekście projektu, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz **Dodaj R Markdown** (lub **Dodaj** > **nowy element** i wybierając polecenie **R Markdown** z listy).

1. Domyślną zawartość nowego pliku są następujące:

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~

## <a name="previews"></a>Wersje zapoznawcze

Visual Studio 2017 w wersji 15.5 lub nowszej automatyczne udostępnianie podglądu na żywo dla R Markdown. Aby włączyć automatyczne przeprowadzanie synchronizacji między edytorze i korzystania z wersji zapoznawczej, wybierz pozycję **R Tools** > **Markdown** > **automatyczna synchronizacja** ( **CTRL**+**Shift**+**Y**). Jeśli nie używasz synchronizacji, można odświeżyć przy użyciu wersji zapoznawczej **R Tools** > **Markdown** > **Podgląd języka Markdown R Załaduj ponownie**.

Możesz także przejrzeć plik w formacie HTML, plików PDF, i w programie Microsoft Word formatuje przez kliknięcie prawym przyciskiem myszy w edytorze i wybierając jedną z **Podgląd** poleceń. Te same polecenia są również dostępne na **R Tools** > **Markdown** menu. (We wcześniejszych wersjach programu Visual Studio te polecenia znajdują się na **R Tools** > **Publikuj** menu.)

![Język RMarkdown na żywo w wersji zapoznawczej i inne polecenia menu (wersja zapoznawcza)](media/rmarkdown-live-preview.png)
