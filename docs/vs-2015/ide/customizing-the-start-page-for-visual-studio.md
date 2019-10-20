---
title: Dostosowywanie strony początkowej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1c3dfb145e70665156c921cc9a6f740539bc4e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665850"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Dostosowanie strony początkowej w Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz dostosować stronę początkową dla programu Visual Studio na kilka domyślnych sposobów, takich jak wyświetlanie okna dialogowego **Otwórz projekt** lub otwieranie rozwiązania, które było ostatnio załadowane. Można także pokazać niestandardową stronę początkową, czyli stronę XAML Windows Presentation Foundation (WPF), która jest uruchamiana w oknie narzędzi i może wykonywać wewnętrzne polecenia Visual Studio.

## <a name="customizing-the-default-start-page"></a>Dostosowywanie domyślnej strony początkowej

1. Na pasku menu wybierz **Narzędzia**, **Opcje**.

2. Rozwiń węzeł **środowisko**, a następnie wybierz polecenie **Uruchamianie**.

3. Z listy podczas **uruchamiania** wybierz element do dostosowania, którego chcesz użyć.

## <a name="show-a-custom-start-page"></a>Pokaż niestandardową stronę początkową

1. Zainstaluj niestandardową stronę początkową na jeden z następujących sposobów:

    - Zainstaluj ją z [Visual Studio Marketplace](https://marketplace.visualstudio.com/), innej witryny lub strony w lokalnym intranecie.

        > [!NOTE]
        > Jeśli odpowiada ci strona przeznaczona dla starszej wersji Visual Studio, możesz ją uaktualnić przy użyciu Visual Studio SDK. Zobacz [jak: uaktualnianie niestandardowej strony początkowej programu Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).

         Otwórz plik. vsix zawierający niestandardową stronę początkową lub skopiuj i Wklej pliki strony początkowej do folderu **% USERPROFILE% \Moje Documents\Visual Studio 2015 \ StartPage** na komputerze.

    - Utwórz własną stronę początkową, jeśli zainstalowałeś Visual Studio SDK.

         Zobacz [Tworzenie własnej strony początkowej](../misc/creating-your-own-start-page.md).

2. Na pasku menu wybierz **Narzędzia**, **Opcje**.

3. Rozwiń węzeł **środowisko**, a następnie wybierz polecenie **Uruchamianie**.

4. Na liście **Dostosuj stronę początkową** wybierz żądaną stronę.

> [!NOTE]
> Jeśli błąd na niestandardowej stronie początkowej powoduje, że Visual Studio ulega awarii, możesz uruchomić Visual Studio w trybie awaryjnym, a następnie ustawić go tak, aby używał domyślnej strony początkowej. Zobacz [/safemode (devenv. exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie ustawień programistycznych w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Tworzenie własnej strony początkowej](../misc/creating-your-own-start-page.md)
