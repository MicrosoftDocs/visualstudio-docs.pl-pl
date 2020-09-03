---
title: Znaczniki R Markdown
description: Jak utworzyć R Markdown dokumenty w programie Visual Studio, aby generować raporty wysokiej jakości, prezentacje i pulpity nawigacyjne.
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 2cfad81c44822e59abb704e5e830357bfd32067d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801558"
---
# <a name="create-r-markdown-documents"></a>Tworzenie R Markdown dokumentów

[R MARKDOWN](https://rmarkdown.rstudio.com/) to format dokumentu służący do przekształcania analizy w języku R na dokumenty, raporty, prezentacje i pulpity nawigacyjne o wysokiej jakości.

R Tools for Visual Studio (RTVS) udostępnia szablon elementu R Markdown, obsługę edytora (w tym IntelliSense for R Code w edytorze), możliwości generowania plików i Podgląd na żywo.

## <a name="using-r-markdown"></a>Używanie R Markdown

1. Zamknij program Visual Studio.
1. (Tylko jeden raz) Zainstaluj program `pandoc` z [pandoc.org](https://pandoc.org/installing.html).
1. Uruchom ponownie program Visual Studio, który powinien pobrać instalację pandoc.
1. Zainstaluj `knitr` pakiety i `rmarkdown` , które możesz wykonać z [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. Utwórz nowy plik R MARKDOWN za pomocą polecenia menu **plik**  >  **Nowy**  >  **plik** i wybierz pozycję **R**  >  **R MARKDOWN** z listy. W kontekście projektu kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **Dodaj R MARKDOWN** (lub **Dodaj**  >  **nowy element** i wybierz pozycję **R MARKDOWN** z listy).

1. Domyślna zawartość nowego pliku jest następująca:

    <!-- markdownlint-disable MD048 -->
    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you select the **R Tools | Publish | Preview** button, a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~
    <!-- markdownlint-disable MD048 -->

## <a name="previews"></a>Podglądy

Program Visual Studio 2017 w wersji 15,5 i nowszej automatycznie udostępnia podgląd na żywo dla R Markdown. Aby włączyć automatyczną synchronizację między edytorem a podglądem, wybierz pozycję **R Tools**— zapoznawcza  >  **Markdown**  >  **Automatyczna synchronizacja** (**Ctrl** + **SHIFT** + **Y**). Jeśli synchronizacja automatyczna nie jest przeprowadzana, można odświeżyć Podgląd przy użyciu **narzędzi R Tools**w  >  **promocji**  >  **Załaduj ponownie R MARKDOWN wersja zapoznawcza**.

Możesz również wyświetlić podgląd pliku w formatach HTML, PDF i Microsoft Word, klikając prawym przyciskiem myszy w edytorze i wybierając jedno z poleceń **podglądu** . Te same polecenia są również dostępne w menu **R Tools**  >  **przecenowy** narzędzia R Tools. (We wcześniejszych wersjach programu Visual Studio te polecenia są dostępne w **narzędziach**  >  języka R Menu **Publikuj** .)

![RMarkdown Live Preview i inne polecenia menu Podgląd](media/rmarkdown-live-preview.png)
