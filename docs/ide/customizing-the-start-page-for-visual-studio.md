---
title: Zainstaluj niestandardową stronę początkową lub zmień element startowy
ms.date: 02/01/2017
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 8fca98116a6d810a97abbf4e1f850b2312f42c60
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070985"
---
# <a name="customize-the-start-page-for-visual-studio"></a>Dostosuj stronę początkową dla programu Visual Studio

Możesz dostosować środowisko uruchamiania dla programu Visual Studio na kilka różnych sposobów, takich jak pokazywanie **Otwórz projekt** okno dialogowe lub otwieranie rozwiązania, które było ostatnio załadowane. Można także pokazać niestandardową stronę początkową, czyli stronę XAML Windows Presentation Foundation (WPF), która jest uruchamiana w oknie narzędzi i może wykonywać wewnętrzne polecenia Visual Studio.

## <a name="to-change-the-startup-item"></a>Aby zmienić element startowy

1. Na pasku menu wybierz **narzędzia** > **opcje**.

1. Rozwiń **środowiska**, a następnie wybierz **uruchamiania**.

1. W **przy uruchamianiu** listy, wybierz element który będzie wyświetlany po uruchomieniu programu Visual Studio.

## <a name="to-show-a-custom-start-page"></a>Aby pokazać niestandardową stronę początkową

Możesz [utworzyć własną niestandardową stronę początkową](../extensibility/creating-a-custom-start-page.md) przy użyciu zestawu SDK programu Visual Studio lub użyj jednego z nich, że ktoś już został utworzony. Na przykład można znaleźć niestandardowych stron początkowych w [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Aby zainstalować niestandardową stronę początkową, otwórz *.vsix* pliku, lub skopiuj i Wklej pliki strony początkowe do *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* folderu na komputerze.

### <a name="to-select-which-custom-start-page-to-display"></a>Aby wybrać, które niestandardową stronę początkową do wyświetlenia

1. Na pasku menu wybierz **narzędzia** > **opcje**.

1. Rozwiń **środowiska**, a następnie wybierz **uruchamiania**.

1. W **Dostosuj stronę początkową** listy, wybierz stronę, która ma.

> [!NOTE]
> Jeśli błąd na niestandardowej stronie początkowej powoduje, że Visual Studio ulega awarii, możesz uruchomić Visual Studio w trybie awaryjnym, a następnie ustawić go tak, aby używał domyślnej strony początkowej. Zobacz [/safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md)