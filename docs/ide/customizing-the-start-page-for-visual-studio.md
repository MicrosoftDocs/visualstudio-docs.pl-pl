---
title: Zmienianie środowiska uruchamiania
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567219"
---
# <a name="customize-startup"></a>Dostosowywanie uruchamiania

Środowisko uruchamiania programu Visual Studio można dostosować na kilka różnych sposobów, takich jak otwieranie najnowszego rozwiązania lub po prostu puste środowisko programistyczne.

::: moniker range="vs-2017"

Można także pokazać niestandardową stronę początkową, czyli stronę XAML Windows Presentation Foundation (WPF), która jest uruchamiana w oknie narzędzi i może wykonywać wewnętrzne polecenia Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Aby zmienić element startowy

1. Na pasku menu wybierz pozycję**Opcje** **narzędzi** > .

2. Rozwiń **węzeł Środowisko**, a następnie wybierz pozycję **Startup**.

::: moniker range="vs-2017"

3. Na liście **Przy starcie** wybierz element, który ma być wyświetlany po uruchomieniu programu Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

3. Na **liście Przy starcie otwórz** wybierz, co ma się zdarzyć po uruchomieniu programu Visual Studio. Można wybrać **okno Start** (które pozwala otworzyć nowy lub istniejący projekt), **Najnowsze rozwiązanie**lub **Puste środowisko**.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Aby wyświetlić niestandardową stronę początkową

Można [utworzyć własną stronę początkową niestandardowe](../extensibility/creating-a-custom-start-page.md) przy użyciu visual studio SDK lub użyć jednego, który ktoś już utworzył. Na przykład niestandardowe strony startowe można znaleźć w portalu [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Aby zainstalować niestandardową stronę startową, otwórz plik *vsix* lub skopiuj i wklej pliki stron początkowych do folderu *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* na komputerze.

### <a name="to-select-which-custom-start-page-to-display"></a>Aby wybrać niestandardową stronę startową do wyświetlenia

1. Na pasku menu wybierz pozycję **Opcje** **narzędzi** > .

1. Rozwiń **węzeł Środowisko**, a następnie wybierz pozycję **Startup**.

1. Na liście **Dostosowywanie strony początkowej** wybierz odpowiednią stronę.

> [!TIP]
> Jeśli błąd na niestandardowej stronie startowej powoduje awarię programu Visual Studio, można otworzyć program Visual Studio w trybie awaryjnym, a następnie ustawić go tak, aby używał domyślnej strony początkowej. Zobacz [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Zobacz też

- [Personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
