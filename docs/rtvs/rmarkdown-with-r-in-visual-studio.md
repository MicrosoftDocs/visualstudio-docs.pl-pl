---
title: Znaczniki R Markdown
description: Jak utworzyć dokumenty R Markdown w programie Visual Studio do tworzenia wysokiej jakości raportów, prezentacji i pulpitów nawigacyjnych.
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 32cfabfe61a8c1dc8f04cd2d024b07a92b1eb7e2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72888574"
---
# <a name="create-r-markdown-documents"></a>Tworzenie dokumentów r markdown

[R Markdown](https://rmarkdown.rstudio.com/) to format dokumentu, który zamienia analizę w R w wysokiej jakości dokumenty, raporty, prezentacje i pulpity nawigacyjne.

R Tools for Visual Studio (RTVS) udostępnia szablon elementu R Markdown, obsługę edytora (w tym intellisense dla kodu języka R w edytorze), możliwości generowania plików i podgląd na żywo.

## <a name="using-r-markdown"></a>Korzystanie z r markdown

1. Zamknij program Visual Studio.
1. (Tylko jeden raz) Zainstaluj `pandoc` z [pandoc.org](https://pandoc.org/installing.html).
1. Uruchom ponownie program Visual Studio, który powinien odebrać instalację pandoc.
1. Zainstaluj `knitr` i `rmarkdown` pakiety, które można zrobić z [interaktywnego okna:](interactive-repl-for-r-in-visual-studio.md)

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. Utwórz nowy plik R Markdown za pomocą polecenia menu **Plik** > **nowy** > **plik** i wybierz z listy **polecenie R** > **R Markdown.** W kontekście projektu kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz pozycję **Dodaj znaczniki R** (lub **Dodaj** > **nowy element** i wybierz z listy polecenie **R Markdown).**

1. Domyślna zawartość nowego pliku jest następująca:

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

## <a name="previews"></a>Podglądy

Visual Studio 2017 w wersji 15.5 i nowszych automatycznie zapewniają podgląd na żywo dla R Markdown. Aby włączyć automatyczną synchronizację między edytorem a podglądem, wybierz **opcję R Tools** > **Markdown** > **Automatic Sync** (**Ctrl**+**Shift**+**Y**). Jeśli nie korzystasz z synchronizacji automatycznej, możesz odświeżyć podgląd za pomocą **narzędzia R Narzędzia** > **Markdown** > **Reload R Markdown Preview**.

Można również wyświetlić podgląd pliku w formatach HTML, PDF i Microsoft Word, klikając prawym przyciskiem myszy w edytorze i wybierając jedno z poleceń **podglądu.** Te same polecenia są również dostępne w menu **R Tools** > **Markdown.** (We wcześniejszych wersjach programu Visual Studio te polecenia znajdują się w menu > **Publikowanie** **narzędzi języka R).**

![RMarkdown podgląd na żywo i inne polecenia menu podglądu](media/rmarkdown-live-preview.png)
