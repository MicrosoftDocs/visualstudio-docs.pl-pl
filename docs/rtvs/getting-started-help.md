---
title: Okno pomocy dla R
description: Pomoc dla języka R jest zintegrowana bezpośrednio z interaktywnym oknem w programie Visual Studio za pośrednictwem programu ? Polecenia.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: af6c6156b1d88c1d015f7700fc7bed061bbe9a76
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62950605"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Pomoc w programie R Tools for Visual Studio

Pomoc dla języka R jest zintegrowana bezpośrednio z interaktywnym oknem w programie Visual Studio. Za każdym razem, gdy używasz `?` polecenia, takie jak `?mtcars`, pomoc z dokumentacji języka R pojawia się w oknie programu Visual Studio:

![Okno Pomocy w programie Visual Studio](media/help-window.png)

> [!Tip]
> Okno pomocy, podobnie jak wszystkie inne w programie Visual Studio, mogą być rozmieszczone i zadokowane w trybie 1999, jak chcesz. Zobacz [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Aby otworzyć wyniki pomocy w przeglądarce, wybierz menu**Opcje** **narzędzi** >  `External`R i ustaw właściwość R Help **Browser** na . Zobacz [Opcje](options-for-r-tools-in-visual-studio.md).

Aby wyszukać `??` pomoc, użyj polecenia, po którym następuje wyszukiwany termin. Użyj cudzysłowów, jeśli wyszukiwany termin zawiera spacje:

```R
??"Motor Trend"
```

![Pomoc w wynikach wyszukiwania](media/help-search1.png)

Okno pomocy zawiera również pole wprowadzania wyszukiwania, za pomocą którego można bezpośrednio przeprowadzić dalsze wyszukiwania w dokumentacji R:

![Pomoc w wynikach wyszukiwania przy użyciu pola wejściowego](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Zintegrowane wyszukiwanie pomocy

Deweloperzy często przeszukują dokumentację R w poszukiwaniu pomocy w przypadku nazw funkcji, zestawów danych i innych elementów. R Tools for Visual Studio (RTVS) usprawnia proces, integrując wyszukiwania pomocy bezpośrednio do edytora i interaktywnych okien.

- Naciśnięcie **klawisza F1** podczas operacji automatycznego uzupełniania tworzy listę wyników pomocy, które pasują do podciągu.
- Kliknięcie prawym przyciskiem myszy wyszukiwanego hasła (np. funkcji) i wybranie polecenia **Pomoc w** tej funkcji powoduje otwarcie pomocy dla tej funkcji. Można również wywołać **Pomoc dla** dowolnego zaznaczenia.

    ![Wywoływanie pomocy za pomocą menu kontekstowego kliknięcia prawym przyciskiem myszy](media/help-right-click.png)

> [!Tip]
> Aby otworzyć zintegrowaną pomoc w przeglądarce, wybierz opcję `External`**Opcje** **narzędzi** > R i ustaw **przeglądarkę F1 na** . Zobacz [Opcje](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Zintegrowane wyszukiwanie StackOverflow

Oprócz wyszukiwania w dokumentacji R, deweloperzy często wyszukiwania StackOverflow podczas pisania kodu. RTVS usprawnia ten proces. Kliknij prawym przyciskiem myszy termin lub zaznaczenie, wybierz polecenie **Wyszukaj** w sieci Web **(Ctrl**+**F1),** a program Visual Studio otworzy okno z wynikami wyszukiwania o zakresie do StackOverflow:

![Wyniki wyszukiwania w sieci Web w programie Visual Studio](media/help-web-search-results.png)

Załączony ciąg zakresu można zmienić `R site:stackoverflow`za pomocą opcji R **Tools** > **Options** > **F1 Web search string:**

![Zmienianie opcji wyszukiwania w sieci Web F1](media/options-dialog.png)

Jeśli wolisz wyświetlać wyniki w przeglądarce, zmień opcję **F1 Web Browser** zgodnie z [opisem w opcji](options-for-r-tools-in-visual-studio.md).