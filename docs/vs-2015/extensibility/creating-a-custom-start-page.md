---
title: Tworzenie niestandardowej strony początkowej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acb7922658a5dd7db0839051a42a119733c8b1d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184209"
---
# <a name="creating-a-custom-start-page"></a>Tworzenie niestandardowej strony początkowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli nie możesz utworzyć niestandardowej strony początkowej przy użyciu szablonu projektu Strona początkowa, zgodnie z opisem na stronie [startowej](../misc/creating-your-own-start-page.md), możesz ją utworzyć ręcznie, wykonując kroki opisane w tym dokumencie.  
  
## <a name="creating-a-blank-start-page"></a>Tworzenie pustej strony początkowej  
 Najpierw Utwórz pustą stronę początkową, tworząc plik XAML, który ma strukturę tagów, która będzie rozpoznawana przez program Visual Studio. Następnie Dodaj znaczniki i kod w celu utworzenia żądanego wyglądu i funkcjonalności.  
  
#### <a name="to-create-a-blank-start-page"></a>Aby utworzyć pustą stronę początkową  
  
1. Utwórz nowy projekt typu **Aplikacja WPF** (**Visual C#/Windows Desktop**.  
  
2. Dodaj odwołanie do `Microsoft.VisualStudio.Shell.14.0` .  
  
3. Otwórz plik XAML w edytorze XML i Zmień element najwyższego poziomu \<Window> na \<UserControl> element bez usuwania żadnej deklaracji przestrzeni nazw.  
  
4. Usuń `x:Class` deklarację z elementu najwyższego poziomu. Dzięki temu zawartość XAML jest zgodna z oknem narzędzia Visual Studio, które obsługuje stronę początkową.  
  
5. Dodaj następujące deklaracje przestrzeni nazw do elementu najwyższego poziomu \<UserControl> .  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Te przestrzenie nazw umożliwiają dostęp do poleceń, kontrolek i ustawień interfejsu użytkownika programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Dodawanie poleceń programu Visual Studio do strony startowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     W poniższym przykładzie pokazano adiustację w pliku XAML dla pustej strony początkowej. Dowolna Zawartość niestandardowa powinna się przechodzić do <xref:System.Windows.Controls.Grid> elementu wewnętrznego.  
  
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
  
6. Dodaj formanty do pustego \<UserControl> elementu, aby wypełnić niestandardową stronę początkową. Aby dowiedzieć się, jak dodać funkcję specyficzną dla programu Visual Studio, zobacz [Dodawanie poleceń programu Visual Studio do strony startowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testowanie i stosowanie niestandardowej strony początkowej  
 Nie ustawiaj podstawowego wystąpienia programu Visual Studio, aby uruchomić niestandardową stronę początkową do momentu sprawdzenia, czy nie ulegnie awarii program Visual Studio. Zamiast tego przetestuj go w eksperymentalnym wystąpieniu.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Aby przetestować ręcznie utworzoną niestandardową stronę początkową  
  
1. Skopiuj plik XAML i wszystkie pomocnicze pliki tekstowe lub pliki znaczników do folderu **%USERPROFILE%\My Documents\Visual Studio 2015 \ startpages \\ ** .  
  
2. Jeśli strona początkowa odwołuje się do dowolnych kontrolek lub typów w zestawach, które nie są zainstalowane przez program Visual Studio, skopiuj zestawy, a następnie wklej je w _folderze instalacyjnym programu Visual Studio_**\Common7\IDE\PrivateAssemblies \\ **.  
  
3. W wierszu polecenia programu Visual Studio wpisz **devenv/rootsuffix Exp** , aby otworzyć eksperymentalne wystąpienie programu Visual Studio.  
  
4. W eksperymentalnym wystąpieniu przejdź do strony **Narzędzia/Opcje/środowisko/Start** , a następnie wybierz plik XAML na liście rozwijanej **Dostosuj stronę początkową** .  
  
5. W menu **Widok** kliknij pozycję **Strona początkowa**.  
  
     Powinna zostać wyświetlona niestandardowa strona startowa. Jeśli chcesz zmienić dowolne pliki, musisz zamknąć wystąpienie eksperymentalne, wprowadzić zmiany, skopiować i wkleić zmienione pliki, a następnie ponownie otworzyć doświadczalne wystąpienie, aby wyświetlić zmiany.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Aby zastosować niestandardową stronę początkową w podstawowym wystąpieniu programu Visual Studio  
  
- Po przetestowaniu strony początkowej i znalezieniu jej jako stabilnej Użyj opcji **Dostosuj stronę początkową** w oknie dialogowym **Opcje** , aby wybrać ją jako stronę początkową w podstawowym wystąpieniu programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Dodawanie niestandardowego kodu XAML do strony początkowej](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)   
 [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Przewodnik: zapisywanie ustawień użytkownika na stronie startowej](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Wdrażanie niestandardowych stron początkowych](../extensibility/deploying-custom-start-pages.md)
