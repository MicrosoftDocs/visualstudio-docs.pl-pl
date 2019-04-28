---
title: Zmień środowisko uruchamiania
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8b31f033b9c04871e57836dd263071d87a24fda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824259"
---
# <a name="customize-startup"></a>Dostosowywanie uruchamiania

Możesz dostosować środowisko uruchamiania dla programu Visual Studio na kilka różnych sposobów, takich jak otwieranie najnowsze rozwiązania lub po prostu środowiska deweloperskiego puste.

::: moniker range="vs-2017"

Można także pokazać niestandardową stronę początkową, czyli stronę XAML Windows Presentation Foundation (WPF), która jest uruchamiana w oknie narzędzi i może wykonywać wewnętrzne polecenia Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Aby zmienić element startowy

1. Na pasku menu wybierz **narzędzia** > **opcje**.

2. Rozwiń **środowiska**, a następnie wybierz **uruchamiania**.

::: moniker range="vs-2017"

3. W **przy uruchamianiu** listy, wybierz element który będzie wyświetlany po uruchomieniu programu Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

3. W **podczas uruchamiania, należy otworzyć** , wybierz, co ma się stać po uruchomieniu programu Visual Studio. Możesz wybrać spośród **rozpoczęcia okna** (który umożliwia otwarcie nowego lub istniejącego projektu), **najnowsze rozwiązania**, lub **puste środowisko**.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Aby pokazać niestandardową stronę początkową

Możesz [utworzyć własną niestandardową stronę początkową](../extensibility/creating-a-custom-start-page.md) przy użyciu zestawu SDK programu Visual Studio lub użyj jednego z nich, że ktoś już został utworzony. Na przykład można znaleźć niestandardowych stron początkowych w [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Aby zainstalować niestandardową stronę początkową, otwórz *.vsix* pliku, lub skopiuj i Wklej pliki strony początkowe do *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* folderu na komputerze.

### <a name="to-select-which-custom-start-page-to-display"></a>Aby wybrać, które niestandardową stronę początkową do wyświetlenia

1. Na pasku menu wybierz **narzędzia** > **opcje**.

1. Rozwiń **środowiska**, a następnie wybierz **uruchamiania**.

1. W **Dostosuj stronę początkową** listy, wybierz stronę, która ma.

> [!TIP]
> Jeśli wystąpił błąd podczas niestandardową stronę początkową powoduje, że program Visual Studio ulega awarii, można otworzyć programu Visual Studio w trybie awaryjnym, a następnie ustaw go do używania domyślnej strony początkowej. Zobacz [/safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end