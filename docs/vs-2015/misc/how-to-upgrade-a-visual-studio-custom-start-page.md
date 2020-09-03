---
title: 'Instrukcje: uaktualnianie niestandardowej strony początkowej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: a7854de705a961463b1e8435e7340548cfc23bf3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74293374"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Instrukcje: uaktualnianie niestandardowej strony początkowej programu Visual Studio
Możesz uaktualnić niestandardową stronę początkową programu Visual Studio 2010 lub Visual Studio 2012 do programu Visual Studio 2015, wykonując czynności opisane poniżej.

> [!WARNING]
> Niestandardowa strona początkowa uaktualniona w tej procedurze jest tą utworzoną przy użyciu szablonu [niestandardowego strony początkowej](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.CustomStartPageProjectTemplate) w galerii programu Visual Studio. Na stronie startowej mogą znajdować się inne funkcje, które muszą zostać uaktualnione.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Aby uaktualnić niestandardową stronę początkową do programu Visual Studio 2015

1. Upewnij się, że program Visual Studio 2015 i zestaw SDK programu Visual Studio 2015 są zainstalowane. Możesz pobrać VSSDK z [zestawu Microsoft Visual Studio 2013 SDK](https://my.visualstudio.com/Downloads?pid=1436).

2. Otwórz niestandardowy szablon projektu. Zostanie wyświetlony komunikat z informacją o tym, że projekt ma zostać uaktualniony. Kliknij przycisk **OK** i poczekaj na zakończenie uaktualniania.

3. We właściwościach projektu dla projektu strony początkowej i projektu kontrolki upewnij się, że platformą docelową jest co najmniej .NET Framework 4,5.

4. W kategorii Debuguj właściwości projektu strony początkowej, Ustaw ścieżkę do wersji programu Visual Studio 2015 devenv.exe.

5. W odwołaniach projektu dla obu projektów Usuń odwołania do Microsoft. VisualStudio. Shell. 11.0 i Dodaj odwołania do Microsoft. VisualStudio. Shell. 14.0.

6. Otwórz plik StartPage. XAML z edytorem XML i wprowadź następujące zmiany:

    1. Zaktualizuj przestrzenie nazw. Zmień następujące wiersze:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         do następujących:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. Otwórz formant. XAML i Zmień odwołanie do przestrzeni nazw `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` na `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .