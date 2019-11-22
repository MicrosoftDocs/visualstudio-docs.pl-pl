---
title: Tworzenie własnej strony początkowej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: jillfra
ms.openlocfilehash: ceb78d3310f37a58850199b11fb2b2fed86f6799
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299321"
---
# <a name="creating-your-own-start-page"></a>Tworzenie własnej strony początkowej
Możesz utworzyć niestandardową stronę początkową przy użyciu szablonu projektu strony początkowej lub przez utworzenie pustej strony początkowej.  
  
 Projektant XAML może nie zapewniać w pełni precyzyjnej wizualizacji niestandardowych stron początkowych ze względu na zależności w modelu aplikacji programu Visual Studio.  
  
## <a name="using-the-project-template"></a>Korzystanie z szablonu projektu  
 Szablon projektu strony początkowej tworzy projekt strony startowej, który jest kompletną kopią strony początkowej programu Visual Studio. Następnie można edytować stronę początkową w swoich specyfikacjach.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Aby utworzyć niestandardową stronę początkową przy użyciu szablonu projektu Strona początkowa  
  
1. Pobierz i zainstaluj [szablon projektu strony początkowej](https://go.microsoft.com/fwlink/?LinkId=186204) z galerii programu Visual Studio.  
  
    > [!WARNING]
    > W tym momencie szablon projektu strony początkowej programu Visual Studio 2010 nie został uaktualniony. Informacje o sposobie uaktualniania tego szablonu znajdują się w temacie [How to: Upgrade the Custom Start niestandardowej strony programu Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2. Po zainstalowaniu szablonu Utwórz nowy projekt strony początkowej z nim.  
  
3. W lewym okienku okna dialogowego Nowy projekt w obszarze **zainstalowane szablony**rozwiń węzeł **Inne typy projektów** , a następnie kliknij pozycję **rozszerzalność**.  
  
4. W środkowym okienku kliknij pozycję **niestandardowa strona początkowa**, a następnie nazwij projekt i kliknij przycisk **OK**.  
  
     Program Visual Studio tworzy projekt strony startowej, który jest kompletną kopią strony początkowej programu Visual Studio.  
  
5. W obszarze **Eksplorator rozwiązań**Otwórz pozycję **Startpage. XAML**.  
  
6. Edytuj StartPage. XAML.  
  
     Możesz wyświetlić swoją pracę, naciskając klawisz F5, aby otworzyć eksperymentalne wystąpienie programu Visual Studio z zainstalowaną niestandardową stroną startową.  
  
## <a name="creating-a-blank-start-page"></a>Tworzenie pustej strony początkowej  
 Najprostszym sposobem tworzenia pustej strony początkowej jest użycie szablonu projektu Strona początkowa, a następnie usunięcie zawartości.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Aby utworzyć pustą stronę początkową przy użyciu szablonu projektu Strona początkowa  
  
1. Utwórz projekt strony początkowej przy użyciu szablonu projektu Strona początkowa zgodnie z opisem w poprzedniej procedurze.  
  
2. Otwórz StartPage. XAML.  
  
3. Usuń całą zawartość strony, pozostawiając tylko zewnętrzne elementy XML i zawierający siatkę <xref:System.Windows.Controls.Grid>, aby plik. XAML wyglądał podobnie do poniższego przykładu.  
  
   ```xaml
      <Grid xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:sp="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.StartPage"
                xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.10.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.10.0"
            mc:Ignorable="d" 
                d:DesignHeight="600" d:DesignWidth="800">
       <Grid>
           <!--Add content here.-->
       </Grid>
   </Grid>
   ```
      
4. Usuń wszystkie pliki pomocnicze, których nie zamierzasz używać.  
  
    Należy zachować pliki VSIX i pkgdef na potrzeby wdrożenia.  
  
   Alternatywnie można utworzyć pustą stronę początkową, tworząc plik XAML o prawidłowej strukturze tagów, który zostanie rozpoznany przez program Visual Studio. Następnie można dodać znaczniki i kod w celu uzyskania odpowiedniego wyglądu i funkcjonalności. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowej strony początkowej](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testowanie i stosowanie niestandardowej strony początkowej  
 Nie ustawiaj wystąpienia podstawowego na uruchamianie niestandardowej strony początkowej do momentu sprawdzenia, czy nie ulegnie awarii. Po przetestowaniu niestandardowej strony początkowej można zastosować ją do systemu przez powtórzenie ostatnich trzech kroków tej procedury w podstawowym wystąpieniu programu Visual Studio.  
  
#### <a name="to-test-a-custom-start-page"></a>Aby przetestować niestandardową stronę początkową  
  
1. Naciśnij F5.  
  
    Eksperymentalne wystąpienie programu Visual Studio otwiera się z zainstalowaną nową stroną startową, ale nie wybraną.  
  
2. W eksperymentalnym wystąpieniu programu Visual Studio, w menu **Narzędzia** kliknij polecenie **Opcje**.  
  
3. W oknie dialogowym **Opcje** w obszarze **środowisko**wybierz pozycję **Uruchamianie**. Następnie na liście **Dostosuj stronę początkową** wybierz plik XAML, a następnie kliknij przycisk **OK**.  
  
4. W menu **Widok** kliknij pozycję **Strona początkowa**.  
  
    Zostanie wyświetlona strona Rozpoczynanie pracy. Należy zamknąć wystąpienie eksperymentalne, ponownie skopiować wszystkie zmienione pliki, a następnie ponownie otworzyć wystąpienie eksperymentalne, aby zobaczyć nowe zmiany.  
  
   Możesz udostępnić niestandardową stronę początkową, przekazując plik. vsix z katalogu bin\Debug do witryny sieci Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub do innej witryny sieci Web lub udziału intranetowego. Aby uzyskać więcej informacji, zobacz [wdrażanie niestandardowych stron początkowych](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie  strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md)  
 [Przewodnik: dodawanie niestandardowych elementów XAML do strony początkowej](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)