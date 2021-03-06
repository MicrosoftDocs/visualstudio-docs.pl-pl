---
title: Zmień środowisko uruchamiania
description: Dowiedz się, jak dostosować środowisko uruchamiania, aby program Visual Studio otwierał narzędzia, które są najbardziej przydatne.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 855218fb6ff2e90cb06e0f48695b64c75e7036b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886590"
---
# <a name="customize-startup"></a>Dostosowywanie uruchamiania

Środowisko uruchamiania programu Visual Studio można dostosować na kilka różnych sposobów, np. otwierając najnowsze rozwiązanie lub tylko puste środowisko programistyczne.

::: moniker range="vs-2017"

Można także pokazać niestandardową stronę początkową, czyli stronę XAML Windows Presentation Foundation (WPF), która jest uruchamiana w oknie narzędzi i może wykonywać wewnętrzne polecenia Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Aby zmienić element startowy

1. Na pasku menu wybierz **Narzędzia**  >  **Opcje**.

2. Rozwiń węzeł **środowisko**, a następnie wybierz polecenie **Uruchamianie**.

::: moniker range="vs-2017"

3. Z listy podczas **uruchamiania** wybierz element, który ma być wyświetlany po uruchomieniu programu Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

3. Na **stronie podczas uruchamiania Otwórz** listę, wybierz, co ma się zdarzyć po uruchomieniu programu Visual Studio. Możesz wybrać z **okna startowego** (który umożliwia otwarcie nowego lub istniejącego projektu), najnowsze **rozwiązanie** lub **puste środowisko**.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Aby wyświetlić niestandardową stronę początkową

Możesz [utworzyć własną niestandardową stronę początkową](../extensibility/creating-a-custom-start-page.md) przy użyciu zestawu Visual Studio SDK lub użyć, która została już utworzona przez kogoś innego. Na przykład możesz znaleźć niestandardowe strony początkowe na [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Aby zainstalować niestandardową stronę początkową, Otwórz plik *. vsix* lub skopiuj i Wklej pliki strony początkowej do folderu *%USERPROFILE%\Documents\Visual Studio 2017 \ restartpages* na komputerze.

### <a name="to-select-which-custom-start-page-to-display"></a>Aby wybrać niestandardową stronę początkową do wyświetlenia

1. Na pasku menu wybierz **Narzędzia** > **Opcje**.

1. Rozwiń węzeł **środowisko**, a następnie wybierz polecenie **Uruchamianie**.

1. Na liście **Dostosuj stronę początkową** wybierz żądaną stronę.

> [!TIP]
> Jeśli błąd na niestandardowej stronie początkowej powoduje awarię programu Visual Studio, można otworzyć program Visual Studio w trybie awaryjnym, a następnie ustawić go tak, aby korzystał z domyślnej strony początkowej. Zobacz [/safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Zobacz też

- [Personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
