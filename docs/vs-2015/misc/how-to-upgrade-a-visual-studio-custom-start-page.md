---
title: 'Instrukcje: Uaktualnij niestandardową stronę początkową | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: 59756adb803c054dbee3a425a9230346aa3a8325
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874376"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Instrukcje: Uaktualnienie programu Visual Studio niestandardową stronę początkową
Można uaktualnić program Visual Studio 2010 lub Visual Studio 2012 niestandardowe początek strony Visual Studio 2015 wykonując kroki wymienione poniżej.

> [!WARNING]
>  Niestandardową stronę początkową uaktualnione w ramach tej procedury jest ten, który został utworzony za pomocą [niestandardowej strony początkowej](http://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) szablonu galerii Visual Studio. Swoją stronę początkową mogą mieć inne funkcje, które muszą zostać uaktualniony.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Aby uaktualnić niestandardową stronę początkową do programu Visual Studio 2015

1.  Upewnij się, że zainstalowany program Visual Studio 2015 i Visual Studio 2015 SDK. Możesz pobrać VSSDK z [programu Microsoft Visual Studio 2013 SDK](http://go.microsoft.com/?linkid=9863867).

2.  Otwórz swój projekt szablonu niestandardowego. Zostanie wyświetlony komunikat informujący, że projekt jest uaktualniany. Kliknij przycisk **OK** i poczekaj na uaktualnienie zakończyć.

3.  We właściwościach projektu dla projektu strona uruchamiania i projektu kontroli upewnij się, że platforma docelowa jest co najmniej programu .NET Framework 4.5.

4.  W kategorii debugowania właściwości projektu dla projektu strona uruchamiania Ustaw ścieżkę do wersji programu Visual Studio 2015 devenv.exe.

5.  W odwołaniach projektu dla obu projektów Usuń odwołania do Microsoft.VisualStudio.Shell.11.0 i dodać odwołania do Microsoft.VisualStudio.Shell.14.0.

6.  Otwórz StartPage.xaml za pomocą edytora XML i wprowadź następujące zmiany:

    1.  Aktualizowanie przestrzeni nazw. Zmień następujące wiersze:

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

7.  Otwórz MyControl.xaml i zmienić odwołanie do przestrzeni nazw `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` do `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .