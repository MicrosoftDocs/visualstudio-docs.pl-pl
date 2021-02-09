---
title: Okno pomocy dla języka R
description: Pomoc dla języka R jest zintegrowana bezpośrednio z oknem interaktywnym w programie Visual Studio za pomocą? dotyczące.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 551f929e4d42b208dd222f052b27720edb273761
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885771"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Pomoc w R Tools for Visual Studio

Pomoc dla języka R jest zintegrowana bezpośrednio z oknem interaktywnym w programie Visual Studio. Za każdym razem, gdy użyjesz `?` polecenia, na przykład `?mtcars` , w oknie programu Visual Studio pojawi się pomoc z dokumentacji języka R:

![Okno Pomoc w programie Visual Studio](media/help-window.png)

> [!Tip]
> Okno pomocy, podobnie jak wszystkie inne w programie Visual Studio, może być ułożone i zadokowane. Zobacz [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Aby otworzyć wyniki pomocy w przeglądarce, wybierz menu Opcje **Narzędzia R Tools**  >   i ustaw właściwość **Pomoc dla języka R Browser** na `External` . Zobacz [Opcje](options-for-r-tools-in-visual-studio.md).

Aby wyszukać pomoc, użyj `??` polecenia, a następnie wyszukiwanego terminu. Jeśli termin wyszukiwania zawiera spacje, użyj cudzysłowów:

```R
??"Motor Trend"
```

![Wyniki wyszukiwania pomocy](media/help-search1.png)

Okno Pomoc zawiera również pole danych wejściowych wyszukiwania, za pomocą którego można przeprowadzić dalsze wyszukiwanie w dokumentacji języka R bezpośrednio:

![Pomóż w wyszukiwaniu wyników przy użyciu pola wejściowego](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Zintegrowane wyszukiwanie pomocy

Deweloperzy często przeszukują dokumentację języka R, aby uzyskać pomoc dotyczącą nazw funkcji, zestawów danych i innych elementów. R Tools for Visual Studio (RTVS) usprawnia proces przez integrację przeszukiwania pomocy bezpośrednio z edytorem i oknami interaktywnymi.

- Naciśnięcie klawisza **F1** podczas operacji autouzupełniania tworzy listę wyników pomocy, które pasują do podciągu.
- Kliknij prawym przyciskiem myszy termin wyszukiwania (na przykład funkcję), a następnie wybierając polecenie **Pomoc dla** tej funkcji. Możesz również wywołać **Pomoc** dla dowolnego zaznaczenia.

    ![Wywoływanie pomocy za pomocą menu kontekstowego po kliknięciu prawym przyciskiem myszy](media/help-right-click.png)

> [!Tip]
> Aby otworzyć zintegrowaną pomoc w przeglądarce, wybierz **Opcje narzędzia R Tools**  >   i ustaw **przeglądarkę internetową F1** na `External` . Zobacz [Opcje](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Zintegrowane wyszukiwanie StackOverflow

Oprócz wyszukiwania w dokumentacji języka R, deweloperzy często wyszukują StackOverflow podczas pisania kodu. RTVS upraszcza to również proces. Kliknij prawym przyciskiem myszy termin lub wybór, wybierz pozycję **Wyszukaj w sieci Web dla** polecenia (**Ctrl** + **F1**), a program Visual Studio otwiera okno z wynikami wyszukiwania w zakresie StackOverflow:

![Wyniki wyszukiwania w sieci Web w programie Visual Studio](media/help-web-search-results.png)

Można zmienić dołączany ciąg zakresu, `R site:stackoverflow` za pomocą opcji **Narzędzia R Tools**  >    >  **F1 ciąg wyszukiwania w sieci Web** :

![Zmiana opcji ciągu wyszukiwania w sieci Web F1](media/options-dialog.png)

Jeśli wolisz wyświetlać wyniki w przeglądarce, Zmień opcję **przeglądarki sieci Web F1** zgodnie z opisem w temacie [Opcje](options-for-r-tools-in-visual-studio.md).