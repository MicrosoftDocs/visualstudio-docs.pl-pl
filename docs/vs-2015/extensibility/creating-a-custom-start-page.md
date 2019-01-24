---
title: Tworzenie niestandardowej strony początkowej | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e7fbc9f18a668cbe3738ab3c8dd734ddadd8ce08
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759009"
---
# <a name="creating-a-custom-start-page"></a>Tworzenie niestandardowej strony początkowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli nie można utworzyć niestandardowej strony początkowej za pomocą szablonu projektu strony początkowej, zgodnie z opisem w [Start stron](../misc/creating-your-own-start-page.md), można ręcznie utworzyć jeden, wykonując kroki opisane w tym dokumencie.  
  
## <a name="creating-a-blank-start-page"></a>Tworzenie strony początkowej puste  
 Po pierwsze upewnij pustą stronę początkową, tworząc plik .xaml, który ma strukturę tag, która będzie także rozpoznawał programu Visual Studio. Następnie dodaj znaczniki i kodem, aby wygenerować wygląd i funkcje, które mają.  
  
#### <a name="to-create-a-blank-start-page"></a>Aby utworzyć pustą stronę początkową  
  
1.  Utwórz nowy projekt typu **aplikacji WPF** (**Visual C# / Windows Desktop**.  
  
2.  Dodaj odwołanie do `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Otwórz plik XAML w edytorze XML i zmień najwyższego poziomu \<okna > elementu \<UserControl > element bez usuwania deklaracje przestrzeni nazw.  
  
4.  Usuń `x:Class` deklaracji z elementem najwyższego poziomu. To sprawia, że zawartość XAML zgodny z okna narzędzi programu Visual Studio, który jest hostem strony początkowej.  
  
5.  Dodaj następujące deklaracje przestrzeni nazw najwyższego poziomu \<UserControl > element.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Te przestrzenie nazw umożliwiają dostęp do poleceń programu Visual Studio, formantów i ustawienia interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [dodanie polecenia programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     Poniższy przykład pokazuje znaczniki w pliku .xaml dla pustą stronę początkową. Żadnej zawartości niestandardowego należy go w programie wewnętrzny <xref:System.Windows.Controls.Grid> elementu.  
  
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
  
6.  Dodawanie formantów do pustych \<UserControl > element, aby wypełnić niestandardowej strony początkowej. Aby uzyskać informacje dotyczące sposobu dodawania funkcji, które są specyficzne dla programu Visual Studio, zobacz [dodanie polecenia programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testowanie i stosowanie niestandardowy strona początkowa  
 Nie należy ustawiać podstawowe wystąpienie programu Visual Studio, aby uruchomić niestandardowej strony początkowej do momentu upewnieniu się, że nie powoduje awarii programu Visual Studio. Zamiast tego należy przetestować w doświadczalnym wystąpieniu.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Aby przetestować ręczne tworzenie niestandardowej strony początkowej  
  
1.  Skopiuj plik XAML i pomocnicze pliki tekstowe lub znaczników pliki do **%USERPROFILE%\My 2015\StartPages Documents\Visual Studio\\**  folderu.  
  
2.  Jeśli swoją stronę początkową odwołuje się do żadnych formantów lub typów w zestawach, które nie są instalowane przez program Visual Studio, skopiować te zestawy, a następnie wklej je w _folder instalacji programu Visual Studio_**\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  Wpisz w wierszu polecenia programu Visual Studio **devenv /rootsuffix Exp** otworzyć doświadczalne wystąpienie programu Visual Studio.  
  
4.  W doświadczalnym wystąpieniu, przejdź do **narzędzia / Opcje / środowisko / uruchamiania** strony i wybierz plik XAML z **Dostosuj stronę początkową** listy rozwijanej.  
  
5.  Na **widoku** menu, kliknij przycisk **strona startowa**.  
  
     Powinien być wyświetlany z niestandardową stronę początkową. Jeśli chcesz zmienić wszystkie pliki, możesz musi Zamknij wystąpienie doświadczalne, wprowadzić zmiany, skopiuj Wklej zmienionych plików i następnie ponownie otwórz wystąpienie doświadczalne, aby wyświetlić zmiany.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Aby zastosować niestandardowy strona startowa podstawowego wystąpienia programu Visual Studio  
  
-   Po po przetestowaniu stronę początkową i on stabilny, użyj **Dostosuj stronę początkową** opcji **opcje** okno dialogowe, aby ją zaznaczyć jako stronę startową w podstawowego wystąpienia programu Visual Studio  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Dodawanie niestandardowych XAML do strony początkowej](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)   
 [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Przewodnik: Zapisywanie ustawień użytkownika na stronie początkowej](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Wdrażanie niestandardowych stron początkowych](../extensibility/deploying-custom-start-pages.md)
