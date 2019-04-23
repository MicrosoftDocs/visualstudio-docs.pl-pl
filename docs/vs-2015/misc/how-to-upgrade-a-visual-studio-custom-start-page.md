---
title: 'Instrukcje: Uaktualnij niestandardową stronę początkową | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: 457b3baf2b291a0ef96bd8bbd748261348a2108d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045463"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Instrukcje: Uaktualnienie programu Visual Studio niestandardową stronę początkową
Można uaktualnić program Visual Studio 2010 lub Visual Studio 2012 niestandardowe początek strony Visual Studio 2015 wykonując kroki wymienione poniżej.

> [!WARNING]
>  Niestandardową stronę początkową uaktualnione w ramach tej procedury jest ten, który został utworzony za pomocą [niestandardowej strony początkowej](http://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) szablonu galerii Visual Studio. Swoją stronę początkową mogą mieć inne funkcje, które muszą zostać uaktualniony.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Aby uaktualnić niestandardową stronę początkową do programu Visual Studio 2015

1. Upewnij się, że zainstalowany program Visual Studio 2015 i Visual Studio 2015 SDK. Możesz pobrać VSSDK z [programu Microsoft Visual Studio 2013 SDK](https://my.visualstudio.com/Downloads?pid=1436).

2. Otwórz swój projekt szablonu niestandardowego. Zostanie wyświetlony komunikat informujący, że projekt jest uaktualniany. Kliknij przycisk **OK** i poczekaj na uaktualnienie zakończyć.

3. We właściwościach projektu dla projektu strona uruchamiania i projektu kontroli upewnij się, że platforma docelowa jest co najmniej programu .NET Framework 4.5.

4. W kategorii debugowania właściwości projektu dla projektu strona uruchamiania Ustaw ścieżkę do wersji programu Visual Studio 2015 devenv.exe.

5. W odwołaniach projektu dla obu projektów Usuń odwołania do Microsoft.VisualStudio.Shell.11.0 i dodać odwołania do Microsoft.VisualStudio.Shell.14.0.

6. Otwórz StartPage.xaml za pomocą edytora XML i wprowadź następujące zmiany:

    1. Aktualizowanie przestrzeni nazw. Zmień następujące wiersze:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         do następującego:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. Otwórz MyControl.xaml i zmienić odwołanie do przestrzeni nazw `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` do `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .