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
ms.openlocfilehash: 32cfabfe61a8c1dc8f04cd2d024b07a92b1eb7e2
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888574"
---
# <a name="create-r-markdown-documents"></a>Tworzenie R Markdown dokumentów

[R MARKDOWN](https://rmarkdown.rstudio.com/) to format dokumentu służący do przekształcania analizy w języku R na dokumenty, raporty, prezentacje i pulpity nawigacyjne o wysokiej jakości.

R Tools for Visual Studio (RTVS) udostępnia szablon elementu R Markdown, obsługę edytora (w tym IntelliSense for R Code w edytorze), możliwości generowania plików i Podgląd na żywo.

## <a name="using-r-markdown"></a>Używanie R Markdown

1. Zamknij program Visual Studio.
1. (Tylko jeden raz) Zainstaluj `pandoc` z [pandoc.org](https://pandoc.org/installing.html).
1. Uruchom ponownie program Visual Studio, który powinien pobrać instalację pandoc.
1. Zainstaluj `knitr` i `rmarkdown` pakiety, które możesz wykonać w [oknie interaktywnym](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. Utwórz nowy plik R Markdown przy użyciu polecenia **plik** > **Nowy** > **plik** , a następnie wybierz pozycję **R** > **R MARKDOWN** z listy. W kontekście projektu kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **dodaj R MARKDOWN** (lub **Dodaj** > **nowy element** i wybierz pozycję **R MARKDOWN** z listy).

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

## <a name="previews"></a>Wersje zapoznawcze

Program Visual Studio 2017 w wersji 15,5 i nowszej automatycznie udostępnia podgląd na żywo dla R Markdown. Aby włączyć automatyczną synchronizację między edytorem a podglądem, wybierz pozycję **R Tools** > w obszarze **promocji** > **automatycznej synchronizacji** (**Ctrl**+**SHIFT**+**Y**). Jeśli nie używasz automatycznej synchronizacji, możesz odświeżyć Podgląd przy użyciu **narzędzi R Tools** > **promocji** > **Załaduj ponownie R MARKDOWN wersji zapoznawczej**.

Możesz również wyświetlić podgląd pliku w formatach HTML, PDF i Microsoft Word, klikając prawym przyciskiem myszy w edytorze i wybierając jedno z poleceń **podglądu** . Te same polecenia są również dostępne w menu **Narzędzia R** > w **promocji** . (We wcześniejszych wersjach programu Visual Studio te polecenia są dostępne w menu **Narzędzia R** > **Publikowanie** .)

![RMarkdown Live Preview i inne polecenia menu Podgląd](media/rmarkdown-live-preview.png)
