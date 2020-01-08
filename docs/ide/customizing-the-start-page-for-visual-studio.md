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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 281a0c43c0163d158151683e9fdc483dfc1709f5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567219"
---
# <a name="customize-startup"></a>Dostosowywanie uruchamiania

Środowisko uruchamiania programu Visual Studio można dostosować na kilka różnych sposobów, np. otwierając najnowsze rozwiązanie lub tylko puste środowisko programistyczne.

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

3. Na **stronie podczas uruchamiania Otwórz** listę, wybierz, co ma się zdarzyć po uruchomieniu programu Visual Studio. Możesz wybrać z **okna startowego** (który umożliwia otwarcie nowego lub istniejącego projektu), najnowsze **rozwiązanie**lub **puste środowisko**.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Aby pokazać niestandardową stronę początkową

Możesz [utworzyć własną niestandardową stronę początkową](../extensibility/creating-a-custom-start-page.md) przy użyciu zestawu SDK programu Visual Studio lub użyj jednego z nich, że ktoś już został utworzony. Na przykład można znaleźć niestandardowych stron początkowych w [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Aby zainstalować niestandardową stronę początkową, otwórz *.vsix* pliku, lub skopiuj i Wklej pliki strony początkowe do *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* folderu na komputerze.

### <a name="to-select-which-custom-start-page-to-display"></a>Aby wybrać, które niestandardową stronę początkową do wyświetlenia

1. Na pasku menu wybierz polecenie **narzędzia** > **Opcje**.

1. Rozwiń **środowiska**, a następnie wybierz **uruchamiania**.

1. W **Dostosuj stronę początkową** listy, wybierz stronę, która ma.

> [!TIP]
> Jeśli błąd na niestandardowej stronie początkowej powoduje awarię programu Visual Studio, można otworzyć program Visual Studio w trybie awaryjnym, a następnie ustawić go tak, aby korzystał z domyślnej strony początkowej. Zobacz [/safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
