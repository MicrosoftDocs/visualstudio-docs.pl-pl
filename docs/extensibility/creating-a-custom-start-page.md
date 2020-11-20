---
title: Tworzenie niestandardowej strony początkowej | Microsoft Docs
description: Dowiedz się, jak utworzyć niestandardową stronę początkową. Rozpocznij od pustej strony początkowej, Dodaj formanty do pustego elementu UserControl, a następnie przetestuj swoją stronę.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b7e4c9690e573d2807eb3ad9d842921ee08417d8
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974560"
---
# <a name="creating-a-custom-start-page"></a>Tworzenie niestandardowej strony początkowej

Możesz utworzyć niestandardową stronę początkową, wykonując czynności opisane w tym dokumencie.

## <a name="create-a-blank-start-page"></a>Utwórz pustą stronę początkową

Najpierw Utwórz pustą stronę początkową, tworząc plik *XAML* , który ma strukturę tagów, która będzie rozpoznawana przez program Visual Studio. Następnie Dodaj znaczniki i kod w celu utworzenia żądanego wyglądu i funkcjonalności.

1. Utwórz nowy projekt typu **Aplikacja WPF** (**Visual C#**  >  **Windows Desktop**).

2. Dodaj odwołanie do `Microsoft.VisualStudio.Shell.14.0` .

3. Otwórz plik XAML w edytorze XML i Zmień element najwyższego poziomu \<Window> na \<UserControl> element bez usuwania żadnej deklaracji przestrzeni nazw.

4. Usuń `x:Class` deklarację z elementu najwyższego poziomu. Dzięki temu zawartość XAML jest zgodna z oknem narzędzia Visual Studio, które obsługuje stronę początkową.

5. Dodaj następujące deklaracje przestrzeni nazw do elementu najwyższego poziomu \<UserControl> .

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Te przestrzenie nazw umożliwiają dostęp do poleceń, kontrolek i ustawień interfejsu użytkownika programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     W poniższym przykładzie pokazano adiustację w pliku *XAML* dla pustej strony początkowej. Dowolna Zawartość niestandardowa powinna się przechodzić do <xref:System.Windows.Controls.Grid> elementu wewnętrznego.

    ```vb
    <UserControl
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        xmlns:local="clr-namespace:StartPageHost"
        mc:Ignorable="d"
         Height="350" Width="525">
        <Grid>
        <!--Add content here.-->
        </Grid>
    </UserControl>
    ```

6. Dodaj formanty do pustego \<UserControl> elementu, aby wypełnić niestandardową stronę początkową. Aby dowiedzieć się, jak dodać funkcje specyficzne dla programu Visual Studio, zobacz [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Testowanie i stosowanie niestandardowej strony początkowej

Nie ustawiaj podstawowego wystąpienia programu Visual Studio, aby uruchomić niestandardową stronę początkową do momentu sprawdzenia, czy nie ulegnie awarii program Visual Studio. Zamiast tego przetestuj go w eksperymentalnym wystąpieniu.

### <a name="to-test-a-manually-created-custom-start-page"></a>Aby przetestować ręcznie utworzoną niestandardową stronę początkową

1. Skopiuj plik XAML i wszystkie pomocnicze pliki tekstowe lub pliki znaczników do folderu *%USERPROFILE%\My Documents\Visual Studio 2015 \ startpages \\* .

2. Jeśli strona początkowa odwołuje się do dowolnych formantów lub typów w zestawach, które nie są zainstalowane przez program Visual Studio, skopiuj zestawy, a następnie wklej je w *{folder instalacyjny programu Visual Studio} \Common7\IDE\PrivateAssemblies \\*.

3. W wierszu polecenia programu Visual Studio wpisz **devenv/rootsuffix Exp** , aby otworzyć eksperymentalne wystąpienie programu Visual Studio.

4. W eksperymentalnym wystąpieniu przejdź do **Tools**  >  **Options**  >  **Environment**  >  strony **startowej** Opcje narzędzia, a następnie wybierz plik XAML na liście rozwijanej **Dostosuj stronę początkową** .

5. W menu **Widok** kliknij pozycję **Strona początkowa**.

     Powinna zostać wyświetlona niestandardowa strona startowa. Jeśli chcesz zmienić dowolne pliki, musisz zamknąć wystąpienie eksperymentalne, wprowadzić zmiany, skopiować i wkleić zmienione pliki, a następnie ponownie otworzyć doświadczalne wystąpienie, aby wyświetlić zmiany.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Aby zastosować niestandardową stronę początkową w podstawowym wystąpieniu programu Visual Studio

- Po przetestowaniu strony początkowej i znalezieniu jej jako stabilnej Użyj opcji **Dostosuj stronę początkową** w oknie dialogowym **Opcje** , aby wybrać ją jako stronę początkową w podstawowym wystąpieniu programu Visual Studio.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Dodawanie niestandardowego kodu XAML do strony początkowej](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)
- [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Przewodnik: zapisywanie ustawień użytkownika na stronie początkowej](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Wdróż niestandardowe strony początkowe](../extensibility/deploying-custom-start-pages.md)
