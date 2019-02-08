---
title: Okno pomocy dla języka R
description: Pomoc dla języka R jest zintegrowany bezpośrednio w oknie interaktywnym w programie Visual Studio za pośrednictwem? polecenie.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: af6c6156b1d88c1d015f7700fc7bed061bbe9a76
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55957747"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Pomoc w R Tools for Visual Studio

Pomoc dla języka R jest zintegrowana bezpośrednio w oknie interaktywnym w programie Visual Studio. Zawsze, gdy używasz `?` polecenia, takie jak `?mtcars`, pomocy dokumentace R pojawia się w oknie programu Visual Studio:

![Okno pomocy w programie Visual Studio](media/help-window.png)

> [!Tip]
> Okna Pomocy, takich jak wszystkie inne w programie Visual Studio, można uporządkowane i zadokowane w dowolny sposób. Zobacz [dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Aby otworzyć Pomoc wyników w przeglądarce, wybierz **R Tools** > **opcje** menu i ustaw **przeglądarka pomocy R** właściwość `External`. Zobacz [opcje](options-for-r-tools-in-visual-studio.md).

Aby przeprowadzić wyszukiwanie pomocy, użyj `??` polecenia następuje termin wyszukiwania. Jeśli termin wyszukiwania zawiera spacje, użyj cudzysłowów:

```R
??"Motor Trend"
```

![Wyniki wyszukiwania pomocy](media/help-search1.png)

W oknie Pomoc ma również pole wejściowe wyszukiwania za pomocą których można przeprowadzić dalsze wyszukiwanie w dokumentacji języka R bezpośrednio:

![Pomoc wyników wyszukiwania za pomocą pola wejściowego](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Zintegrowana pomoc wyszukiwania

Deweloperzy często wyszukiwanie w dokumentacji języka R, aby uzyskać pomoc dotyczącą nazwy funkcji, zestawy danych i innych elementów. Narzędzia R Tools for Visual Studio (RTVS) usprawnia proces integrując wyszukiwań pomoc bezpośrednio w edytorze i interaktywnych okien.

- Naciśnięcie klawisza **F1** podczas operacji automatycznego uzupełniania tworzy listę wyników pomocy, które Dopasuj podciąg.
- Kliknij prawym przyciskiem myszy termin wyszukiwania (takich jak funkcja) i wybierając polecenie **pomoc na temat** polecenia Otwiera Pomoc dla tej funkcji. Można również wywołać **pomoc na temat** dla żadnych ustawień.

    ![Wywoływanie pomocy za pośrednictwem menu kontekstowym wywoływanym prawym przyciskiem myszy](media/help-right-click.png)

> [!Tip]
> Aby otworzyć zintegrowana pomoc w przeglądarce, wybierz **R Tools** > **opcje** i ustaw **przeglądarki sieci Web F1** do `External`. Zobacz [opcje](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Wyszukiwanie zintegrowane StackOverflow

Oprócz wyszukiwania w dokumentacji języka R, deweloperzy często wyszukiwania StackOverflow podczas pisania kodu. RTVS usprawnia ten proces, jak również. Kliknij prawym przyciskiem myszy termin lub wyboru, wybierz opcję **Hledat na webu** polecenia (**Ctrl**+**F1**), i Visual Studio powoduje otwarcie okna z wynikami wyszukiwania z zakresem Witryna StackOverflow:

![Wyniki wyszukiwania w Internecie w programie Visual Studio](media/help-web-search-results.png)

Dołączany ciąg zakresu, można zmienić `R site:stackoverflow`za pośrednictwem **R Tools** > **opcje** > **ciąg wyszukiwania w sieci Web F1** opcji:

![Zmiana opcji ciągu wyszukiwania F1 w sieci Web](media/options-dialog.png)

Jeśli wolisz wyświetlić wyniki w przeglądarce, zmień **przeglądarki sieci Web F1** opcji zgodnie z opisem na [opcje](options-for-r-tools-in-visual-studio.md).