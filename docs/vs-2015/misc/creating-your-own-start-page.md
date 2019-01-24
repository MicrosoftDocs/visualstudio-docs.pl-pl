---
title: Tworzenie własnych strony początkowej | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: dc01d4d635d297f1597d900687673dd4d35d049f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761550"
---
# <a name="creating-your-own-start-page"></a>Tworzenie własną stronę początkową
Za pomocą szablonu projektu strony Start lub tworząc pustą stronę początkową, można utworzyć niestandardowej strony początkowej.  
  
 Projektant XAML nie mogą zawierać pełni dokładne wizualnej reprezentacji niestandardowych stron Start ze względu na zależności w modelu aplikacji Visual Studio.  
  
## <a name="using-the-project-template"></a>Przy użyciu szablonu projektu  
 Szablon projektu strona początkowa tworzy projekt strony początkowej, który to kompletna kopia programu Visual Studio strony początkowej. Następnie można edytować strony początkowej do specyfikacji.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Do utworzenia niestandardowej strony początkowej za pomocą szablonu projektu strona startowa  
  
1.  Pobierz i zainstaluj [szablonu projektu strona startowa](http://go.microsoft.com/fwlink/?LinkId=186204) z galerii Visual Studio.  
  
    > [!WARNING]
    >  W tej chwili nie został uaktualniony szablon projektu Visual Studio 2010 strony początkowej. Aby uzyskać informacje o sposobie uaktualniania tego szablonu, zobacz [jak: Uaktualnienie programu Visual Studio niestandardową stronę początkową](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2.  Po zainstalowaniu szablonu, należy utworzyć nowy projekt strony start z nim.  
  
3.  W lewym okienku okna dialogowego Nowy projekt w obszarze **zainstalowane szablony**, rozwiń węzeł **inne typy projektów** węzłem, a następnie kliknij przycisk **rozszerzalności**.  
  
4.  W środkowym okienku kliknij **niestandardowy strona startowa**, a następnie nazwij swój projekt i kliknij **OK**.  
  
     Program Visual Studio tworzy projekt strony początkowej, który jest pełną kopię programu Visual Studio strony początkowej.  
  
5.  Z **Eksploratora rozwiązań**, otwórz **StartPage.xaml**.  
  
6.  Edytuj StartPage.xaml.  
  
     Możesz wyświetlić swoją pracę, naciskając klawisz F5, aby otworzyć doświadczalne wystąpienie programu Visual Studio za pomocą niestandardowej strony początkowej zainstalowane.  
  
## <a name="creating-a-blank-start-page"></a>Tworzenie strony początkowej puste  
 Najprostszym sposobem utworzenia pusta strona początkowa jest użycie szablonu projektu strony początkowej, a następnie usuń zawartość.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Aby utworzyć pustą stronę początkową za pomocą szablonu projektu strona startowa  
  
1. Utwórz projekt strony początkowej za pomocą szablonu projektu strony początkowej, zgodnie z opisem w poprzedniej procedurze.  
  
2. Otwórz StartPage.xaml.  
  
3. Usuń całą zawartość strony, pozostawiając pouze prvky xml zewnętrznego i zawierający siatki <xref:System.Windows.Controls.Grid> elementu, tak, aby plik .xaml przypomina poniższy przykład.  
  
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
      
4. Usuń wszelkie pliki pomocnicze, które będą używane.  
  
    Należy zachować plików .vsix i .pkgdef do celów wdrożenia.  
  
   Alternatywnie można utworzyć pustą stronę początkową przez utworzenie pliku XAML, ze strukturą poprawny tag, aby zostały rozpoznane przez program Visual Studio. Następnie można dodać znaczniki i kodem, aby uzyskać żądany wygląd i działanie. Aby uzyskać więcej informacji, zobacz [tworzenie niestandardowe strony początkowej](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testowanie i stosowanie niestandardowy strona początkowa  
 Nie należy ustawiać podstawowe wystąpienie, aby uruchomić niestandardowej strony początkowej do momentu upewnieniu się, że nie powoduje awarii. Po przetestowaniu niestandardowej strony początkowej, można go zastosować do systemu, powtarzając ostatnie trzy kroki tej procedury w podstawowego wystąpienia programu Visual Studio.  
  
#### <a name="to-test-a-custom-start-page"></a>Aby przetestować niestandardowej strony początkowej  
  
1. Naciśnij F5.  
  
    Nowa strona startowa zainstalowany, ale nie wybrano doświadczalnym wystąpieniu programu Visual Studio zostanie otwarty.  
  
2. W doświadczalnym wystąpieniu programu Visual Studio na **narzędzia** menu, kliknij przycisk **opcje**.  
  
3. W **opcje** dialogowego **środowiska**, wybierz opcję **uruchamiania**. Następnie na **Dostosuj stronę początkową** listy, wybierz swój plik .xaml, a następnie kliknij przycisk **OK**.  
  
4. Na **widoku** menu, kliknij przycisk **strona startowa**.  
  
    Praca, wyświetlania strony początkowej. Należy Zamknij wystąpienie doświadczalne, ponownego skopiowania zmienionych plików, a następnie ponownie otwórz wystąpienie doświadczalne, aby zobaczyć nowe zmiany.  
  
   Możesz udostępnić niestandardowej strony początkowej, przekazując plik .vsix z katalogu bin\debug [galerii Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) witrynę sieci Web lub do innej witryny sieci Web lub intranet udostępniania. Aby uzyskać więcej informacji, zobacz [wdrażanie niestandardowych stron Start](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Przewodnik: Dodawanie niestandardowych XAML do strony początkowej](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)