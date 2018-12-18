---
title: Dostosowanie strony początkowej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c426ca146380ce01ec2c1f257c6da5538b941c19
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059775"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Dostosowanie strony początkowej w Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można dostosować stronę początkową dla programu Visual Studio na kilka domyślnych sposobów, takich jak pokazywanie **Otwórz projekt** okno dialogowe lub otwieranie rozwiązania, które było ostatnio załadowane. Można także pokazać niestandardową stronę początkową, czyli stronę XAML Windows Presentation Foundation (WPF), która jest uruchamiana w oknie narzędzi i może wykonywać wewnętrzne polecenia Visual Studio.

## <a name="customizing-the-default-start-page"></a>Dostosowywanie domyślnej strony początkowej

1.  Na pasku menu wybierz **narzędzia**, **opcje**.

2.  Rozwiń **środowiska**, a następnie wybierz **uruchamiania**.

3.  W **przy uruchamianiu** listy, wybierz element który chcesz dostosować.

## <a name="show-a-custom-start-page"></a>Pokaż niestandardową stronę początkową

1.  Zainstaluj niestandardową stronę początkową na jeden z następujących sposobów:

    -   Zainstaluj go z [galerii Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), innej witryny sieci Web lub strony w lokalnym intranecie.

        > [!NOTE]
        >  Jeśli odpowiada ci strona przeznaczona dla starszej wersji Visual Studio, możesz ją uaktualnić przy użyciu Visual Studio SDK. Zobacz [porady: uaktualnianie z programu Visual Studio niestandardową stronę początkową](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).

         Otwórz plik .vsix, zawierający niestandardową stronę początkową lub skopiuj i Wklej pliki strony początkowej do **% USERPROFILE % \My Studio 2015\StartPages** folderu na komputerze.

    -   Utwórz własną stronę początkową, jeśli zainstalowałeś Visual Studio SDK.

         Zobacz [tworzenia własnego strony początkowej](../misc/creating-your-own-start-page.md).

2.  Na pasku menu wybierz **narzędzia**, **opcje**.

3.  Rozwiń **środowiska**, a następnie wybierz **uruchamiania**.

4.  W **Dostosuj stronę początkową** listy, wybierz stronę, która ma.

> [!NOTE]
>  Jeśli błąd na niestandardowej stronie początkowej powoduje, że Visual Studio ulega awarii, możesz uruchomić Visual Studio w trybie awaryjnym, a następnie ustawić go tak, aby używał domyślnej strony początkowej. Zobacz [/safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [tworzenia własnego strony początkowej](../misc/creating-your-own-start-page.md)
