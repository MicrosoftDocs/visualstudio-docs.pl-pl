---
title: Tworzenie niestandardowej strony startowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3ac0abfe9eedf1c03a8be3bacddbe06ff5698380
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739630"
---
# <a name="creating-a-custom-start-page"></a>Tworzenie niestandardowej strony początkowej

Niestandardową stronę początkową można utworzyć, wykonując czynności opisane w tym dokumencie.

## <a name="create-a-blank-start-page"></a>Tworzenie pustej strony początkowej

Najpierw utwórz pustą stronę początkową, tworząc plik *xaml,* który ma strukturę znaczników rozpoznawaną przez program Visual Studio. Następnie dodaj znaczniki i kod, aby uzyskać wygląd i funkcje, które chcesz.

1. Utwórz nowy projekt typu **WPF Application** (**Visual C#** > **Windows Desktop**).

2. Dodaj odwołanie `Microsoft.VisualStudio.Shell.14.0`do pliku .

3. Otwórz plik XAML w edytorze XML i \<zmień element> okna \<najwyższego poziomu na element> UserControl bez usuwania żadnej z deklaracji obszaru nazw.

4. Usuń `x:Class` deklarację z elementu najwyższego poziomu. Dzięki temu zawartość XAML jest zgodna z oknem narzędzia programu Visual Studio, w którym znajduje się strona początkowa.

5. Dodaj następujące deklaracje obszaru nazw do \<elementu> usercontrol najwyższego poziomu.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Te przestrzenie nazw umożliwiają dostęp do poleceń, formantów i ustawień interfejsu użytkownika programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     W poniższym przykładzie przedstawiono znaczniki w pliku *xaml* pustej strony początkowej. Wszelkie niestandardowe treści powinny <xref:System.Windows.Controls.Grid> przejść w wewnętrznym elemencie.

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

6. Dodaj kontrolki \<do pustego elementu> UserControl, aby wypełnić niestandardową stronę początkową. Aby uzyskać informacje dotyczące dodawania funkcji specyficznych dla programu Visual Studio, zobacz [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Testowanie i stosowanie niestandardowej strony początkowej

Nie należy ustawiać podstawowego wystąpienia programu Visual Studio, aby uruchamiać niestandardową stronę początkową, dopóki nie zostanie zweryfikowana, czy program Visual Studio nie upaść. Zamiast tego należy przetestować go w wystąpieniu eksperymentalnym.

### <a name="to-test-a-manually-created-custom-start-page"></a>Aby przetestować ręcznie utworzoną niestandardową stronę początkową

1. Skopiuj plik XAML i wszystkie pomocnicze pliki tekstowe lub pliki znaczników do folderu *%USERPROFILE%\Moje dokumenty\Visual Studio 2015\StartPages.\\ *

2. Jeśli strona początkowa odwołuje się do wszystkich formantów lub typów w zestawach, które nie są zainstalowane przez program Visual Studio, skopiuj zestawy, a następnie wklej je w *folderze instalacyjnym programu {Visual Studio}\Common7\IDE\PrivateAssemblies\\*.

3. W wierszu polecenia programu Visual Studio wpisz **devenv /rootsuffix Exp,** aby otworzyć eksperymentalne wystąpienie programu Visual Studio.

4. W przypadku wystąpienia eksperymentalnego przejdź do strony**Uruchamianie** **środowiska** > **opcje** >  **narzędzi** > i wybierz plik XAML z listy rozwijanej **Dostosowywanie strony początkowej.**

5. W menu **Widok** kliknij polecenie **Strona początkowa**.

     Powinna zostać wyświetlona niestandardowa strona początkowa. Jeśli chcesz zmienić wszystkie pliki, musisz zamknąć wystąpienie eksperymentalne, wprowadzić zmiany, skopiować i wkleić zmienione pliki, a następnie ponownie otworzyć wystąpienie eksperymentalne, aby wyświetlić zmiany.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Aby zastosować niestandardową stronę startową w podstawowym wystąpieniu programu Visual Studio

- Po przetestowaniu strony początkowej i znalezieniu jej jako stabilnej użyj opcji **Dostosowywanie strony początkowej** w oknie dialogowym **Opcje,** aby zaznaczyć ją jako stronę początkową w podstawowym wystąpieniu programu Visual Studio

## <a name="see-also"></a>Zobacz też

- [Instruktaż: Dodawanie niestandardowego kodu XAML do strony początkowej](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)
- [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Instruktaż: zapisywanie ustawień użytkownika na stronie początkowej](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Wdrażanie niestandardowych stron początkowych](../extensibility/deploying-custom-start-pages.md)
