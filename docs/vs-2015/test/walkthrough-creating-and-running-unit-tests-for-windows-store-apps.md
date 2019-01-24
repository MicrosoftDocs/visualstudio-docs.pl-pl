---
title: 'Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla aplikacji Windows Store Apps | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, Windows Store apps
- unit tests, running
ms.assetid: dd3e8a6a-b366-433e-a409-b9a9b89da89a
caps.latest.revision: 23
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dcd09c2a19bd96a02075901f6b58da71a1a9bee9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754877"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-windows-store-apps"></a>Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla aplikacji Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio obejmuje obsługę testów jednostkowych zarządzanych [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji i zawiera szablony bibliotek testów jednostkowych dla języka Visual C#, Visual Basic i Visual C++.  
  
> [!TIP]
>  Aby uzyskać więcej informacji o tworzeniu [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji, zobacz [Rozpoczynanie pracy z aplikacjami Windows Store](http://go.microsoft.com/fwlink/?LinkID=241410).  
  
 Program Visual Studio oferuje następujące funkcje testowania jednostki:  
  
- [Tworzenie projektów testów jednostkowych](#CreateAndRunUnitTestWin8Tailored_Create)  
  
- [Edytuj Manifest dla projektu testu jednostkowego](#CreateAndRunUnitTestWin8Tailored_Manifest)  
  
- [Kodowanie testu jednostkowego](#CreateAndRunUnitTestWin8Tailored_Code)  
  
- [Uruchamianie testów jednostkowych](#CreateAndRunUnitTestWin8Tailored_Run)  
  
  W poniższych procedurach opisano kroki tworzenia, uruchamiania i debugowania testów jednostkowych dla zarządzanej systemu Windows 8 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Visual Studio  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Create"></a> Tworzenie projektów testów jednostkowych  
  
#### <a name="to-create-a-unit-test-project-for-a-windows-store-app"></a>Aby utworzyć projekt testu jednostkowego dla aplikacji Windows Store  
  
1.  Z **pliku** menu, wybierz **nowy projekt**.  
  
     Wyświetla okno dialogowe Nowy projekt.  
  
2.  W obszarze Szablony wybierz język programowania, aby utworzyć test jednostki, a następnie wybierz polecenie skojarzonego [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Biblioteka testów jednostkowych. Na przykład wybrać **Visual C#** , następnie wybierz **Windows Store**, a następnie wybierz **Biblioteka testów jednostkowych (Windows Store apps)**.  
  
    > [!NOTE]
    >  Visual Studio zawiera szablony bibliotek testów jednostkowych dla języka Visual C#, Visual Basic i Visual C++.  
  
3.  (Opcjonalnie) W **nazwa** polu tekstowym wprowadź nazwę, którego chcesz użyć dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]projekt testów jednostkowych.  
  
4.  (Opcjonalnie) Modyfikuj ścieżkę, w której chcesz utworzyć projekt, wprowadzając ją w **lokalizacji** pole tekstowe, lub wybierając **Przeglądaj** przycisku.  
  
5.  (Opcjonalnie) W **rozwiązania** polu tekstowym, wprowadź nazwę, którego chcesz użyć dla rozwiązania.  
  
6.  Pozostaw **Utwórz katalog rozwiązania** opcja wybrana i wybierz **OK** przycisku.  
  
     ![Biblioteka testów jednostkowych dostosowane](../test/media/unit-test-win8-1.png "Unit_Test_Win8_1")  
  
     Eksplorator rozwiązań za pomocą nowego [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]projekt testów jednostkowych i Edytor kodu wyświetla domyślny test jednostki pod tytułem Testjednostki1.  
  
     ![Nowy projekt testów jednostkowych dostosowane](../test/media/unit-test-win8-unittestexplorer-newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a> Edytuj Manifest dla projektu testu jednostkowego  
 Może być konieczne edytowanie manifestu dla projektu testów jednostkowych w celu dostarczenia wymaganych zdolności do uruchomienia aplikacji.  
  
#### <a name="to-edit-the-unit-test-projects-windows-store-application-manifest-file"></a>Aby edytować plik manifestu aplikacji Windows Store projektu badania jednostki  
  
1.  W Eksploratorze rozwiązań w nowym [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projektu testu jednostkowego, kliknij prawym przyciskiem myszy plik Package.appxmanifest i wybierz polecenie **Otwórz**.  
  
     Wyświetli się Projektant manifestów do edycji.  
  
2.  W Projektancie manifestów wybierz **możliwości** kartę.  
  
3.  Na liście w obszarze **możliwości**, wybierz możliwości potrzebne do testu jednostkowego i kod jej ma mieć test. Na przykład wybierz **Internet** pole wyboru, jeśli testy jednostkowe i kod jest testowanie muszą mieć możliwość dostępu do Internetu.  
  
    > [!NOTE]
    >  Wybranych funkcji powinny znajdować się możliwości, które są niezbędne do [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] testu jednostkowego, aby działo poprawnie. Nigdy nie mają możliwości uwzględnić możliwości, które nie są częścią [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji przetestowane i zwykle powinny być podzestawem funkcji określonych dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]testowanej aplikacji.  
  
     Aby uzyskać więcej informacji dotyczących projektanta manifestów, zobacz [skonfigurować pakiet aplikacji Windows 8.1 przy użyciu manifest designer](http://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d).  
  
     ![Manifest testów jednostkowych](../test/media/unit-test-win8.png "Unit_Test_Win8_")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Code"></a> Kodowanie testu jednostkowego  
  
#### <a name="to-code-the-unit-test-for-a-windows-store-app"></a>Kod testu jednostkowego dla aplikacji Windows Store  
  
1.  W edytorze kodu Edytuj test jednostkowy oraz Dodaj potwierdzenia i logikę wymagane dla testu.  
  
     Aby uzyskać więcej informacji, zobacz w [przy użyciu klas Asercja](http://go.microsoft.com/fwlink/?LinkID=224991) w bibliotece MSDN.  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Run"></a> Uruchamianie testów jednostkowych  
  
#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Aby skompilować rozwiązanie i uruchomić test jednostki za pomocą Eksploratora testów  
  
1.  Na **testu** menu, wybierz **Windows**, a następnie wybierz **Eksplorator testów**.  
  
     Test Explorer, niewyświetlające Twojego testu są wyświetlane.  
  
2.  Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
     Taki test jednostki znajduje się teraz.  
  
    > [!NOTE]
    >  Należy utworzyć rozwiązanie, które można zaktualizować listy testów jednostkowych w Eksploratorze testów.  
  
    > [!WARNING]
    >  Znany problem programu Visual Studio: Test Explorer należy otworzyć przed utworzeniem projektu testu.  
  
3.  W Eksploratorze testów wybierz utworzony test jednostki.  
  
    > [!TIP]
    >  Test Explorer zawiera łącze do kodu źródłowego obok **źródło:**.  
  
4.  Wybierz **uruchomić wszystkie**.  
  
     ![Unit Test Explorer &#45; run unit test](../test/media/unit-test-win8-unittestexplorer-contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")  
  
    > [!TIP]
    >  Można wybrać jeden lub więcej testów wymienionych w Eksploratorze i kliknij prawym przyciskiem myszy i wybierz **Uruchom wybrane testy**.  
    >   
    >  Ponadto istnieje możliwość **Debuguj wybrane testy**, **Otwórz Test**i użyj **właściwości** opcji.  
    >   
    >  ![Unit Test Explorer &#45; uni test context menu](../test/media/unit-test-win8-unittestexplorer-contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")  
  
     Przebiegi testów jednostkowych. Po zakończeniu programu Test Explorer wyświetla stan badania, czas trwania i zawiera również link do źródła.  
  
     ![Eksplorator testów jednostkowych &#45; testów zakończonych](../test/media/unit-test-win8-unittestexplorer-done.png "Unit_Test_Win8_UnitTestExplorer_Done")  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="videos"></a>Wideo  
 [Witryna Channel 9: Jednostki testowania aplikacji Windows Store utworzone przy użyciu XAML](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Fora  
 [Visual Studio Unit Testing](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="msdn-library"></a>MSDN Library  
 [Biblioteka MSDN — tworzenie i Uruchamianie testów jednostkowych dla istniejącego kodu (Visual Studio 2010)](http://go.microsoft.com/fwlink/?LinkID=223683)  
  
## <a name="see-also"></a>Zobacz też  
 [Testowanie aplikacji Store za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Tworzenie i testowanie aplikacji Windows Store, za pomocą Team Foundation Build](http://msdn.microsoft.com/library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9)
