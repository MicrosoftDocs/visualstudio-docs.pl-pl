---
title: Korzystanie z wyszukiwania w programie Visual Studio
description: Dowiedz się, jak za pomocą programu Visual Studio Search znaleźć ustawienia, menu i kod.
ms.date: 10/08/2020
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
ms.assetid: 3870a8fd-4afa-4f1e-a811-9fdf41a9e82d
monikerRange: vs-2019
author: profexorgeek
ms.author: jusjohns
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 101875b3a600a71c832498d05073187d2cf0b774
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873908"
---
# <a name="use-visual-studio-search"></a>Korzystanie z programu Visual Studio Search

Zintegrowane środowisko programistyczne (IDE) programu Visual Studio zawiera wiele menu, opcji i funkcji, które mogą być trudne do zapamiętania. Funkcja wyszukiwania programu Visual Studio to pojedyncze pole wyszukiwania, które ułatwia deweloperom Znajdowanie menu i opcji środowiska IDE, a także wyszukiwanie kodu. Niezależnie od tego, czy jesteś nowym członkiem programu Visual Studio, czy doświadczonym deweloperem, funkcja ta oferuje szybki sposób wyszukiwania w ramach funkcji środowiska IDE i kodu.

Użyj  + skrótu klawiaturowego Ctrl **Q** , aby uzyskać dostęp do pola wyszukiwania lub kliknij pole danych wyjściowych wyszukiwania programu Visual Studio znajdujące się obok paska menu domyślnie:

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Pole wyszukiwania programu Visual Studio" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> Polecenie wykonywane przez program Visual Studio Search to `Window.QuickLaunch` Funkcja, która jest określana jako szybkie wyszukiwanie lub szybkie uruchamianie.

W przeciwieństwie do innych funkcji wyszukiwania, takich jak Znajdź w plikach lub Eksplorator rozwiązań wyszukiwania, wyszukiwanie w wynikach programu Visual Studio obejmuje funkcje środowiska IDE, opcje menu, nazwy plików i inne. W poniższych sekcjach omówiono różne typy wyników, które może znaleźć program Visual Studio Search.

## <a name="search-menus-options-and-windows"></a>Menu, opcje i okna wyszukiwania

Możesz użyć pola wyszukiwania programu Visual Studio, aby znaleźć ustawienia, opcje i podobne elementy konfiguracji. Na przykład wyszukaj pozycję *Zmień motyw* , aby szybko znaleźć i otworzyć okno dialogowe, które umożliwia zmianę motywu kolorów programu Visual Studio, jak pokazano na poniższym zrzucie ekranu:

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Wyszukiwanie ustawień i opcji programu Visual Studio":::

> [!TIP]
> W większości przypadków wyszukiwanie w programie Visual Studio będzie również przypominać o menu, klawiszy skrótów i lokalizacji każdego elementu w wynikach.

Możesz użyć pola wyszukiwania programu Visual Studio, aby znaleźć elementy menu i polecenia. Na przykład wyszukaj *czysty peruwiański* , aby szybko znaleźć i uruchomić polecenie czystego rozwiązania. Wyniki wyszukiwania również oferują przypomnienie dotyczące lokalizacji tego polecenia w menu, jak pokazano na poniższym zrzucie ekranu:

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Wyszukaj elementy menu i polecenia w programie Visual Studio":::

Na koniec można wyszukać okna lub panele, które mogą przypadkowo zostać zamknięte. Na przykład wyszukaj ciąg *test* , aby znaleźć i otworzyć okno Eksplorator testów:

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Przeszukaj okna i panele programu Visual Studio":::

## <a name="search-files-and-code"></a>Wyszukaj pliki i kod

Program Visual Studio Search przeszukuje także elementy rozwiązania pod kątem nazwy pliku, kodu, metody i innych dopasowań. Na poniższym zrzucie ekranu wyszukiwanie w ramach *promocji cenowej* odnalazło plik MarkdownMetaExtractor.cs, `MarkdownMetaExtractor` klasę i dwie metody w ramach rozwiązania:

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Wyszukiwanie plików przy użyciu programu Visual Studio Search":::

Możesz również wykonać wyszukiwanie "notacji CamelCase Case". Na poniższym zrzucie ekranu wyszukiwanie *służbowe* otrzymało **IAR plik**, klasę i metodę programu **przetwórczego** **języka F**.

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Notacji CamelCase Hump wyszukiwanie przy użyciu programu Visual Studio Search":::

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](reference/visual-studio-commands.md)