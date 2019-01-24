---
title: 'Przewodnik: Tworzenie aplikacji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f4103502b3ebd6371f0b1c0ac27c6da7c8904c6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799158"
---
# <a name="walkthrough-building-an-application"></a>Przewodnik: Tworzenie aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przez ukończenie tego instruktażu, zapoznasz się więcej na temat kilka opcji, które można skonfigurować podczas tworzenia aplikacji za pomocą programu Visual Studio. Będzie utworzyć niestandardową konfigurację kompilacji, ukrywał niektóre komunikaty ostrzegawcze i zwiększał kompilację informacji wyjściowych wśród innych zadań, aby uzyskać przykładową aplikację.  
  
 Ten temat zawiera następujące sekcje:  
  
 [Zainstaluj przykładową aplikację.](../ide/walkthrough-building-an-application.md#BKMK_installapp)  
  
 [Utwórz niestandardową konfigurację kompilacji](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)  
  
 [Kompiluj aplikację](../ide/walkthrough-building-an-application.md#BKMK_building)  
  
 [Ukryj ostrzeżenia kompilatora](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)  
  
 [Wyświetl dodatkowe szczegóły kompilacji w oknie danych wyjściowych](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)  
  
 [Tworzenie kompilacji wydania](../ide/walkthrough-building-an-application.md#BKMK_releasebuild)  
  
##  <a name="BKMK_installapp"></a> Zainstaluj przykładową aplikację.  
 Użyjesz **rozszerzenia i aktualizacje** okno dialogowe, aby znaleźć i zainstalować [wprowadzenie do kompilowania aplikacji WPF](http://code.msdn.microsoft.com/Introduction-to-Building-b8d16419?SRC=VSIDE) próbki z galerii przykładów w witrynie internetowej firmy Microsoft. Galeria przykładów zawiera szereg przykładowych projektów i kodu, który można pobrać i przejrzeć przy planowaniu i opracowywaniu aplikacji.  
  
#### <a name="to-install-the-sample-application"></a>Aby zainstalować przykładową aplikację  
  
1. Na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.  
  
2. Wybierz **Online** kategorii, a następnie wybierz **galerii przykładów** kategorii.  
  
3. Określ `Introduction` w polu wyszukiwania, aby znaleźć plik.  
  
    ![Okno dialogowe rozszerzenia i aktualizacje](../ide/media/buildwalk-extensionsdialogsampledownload.png "BuildWalk_ExtensionsDialogSampleDownload")  
  
4. Na liście wyników wybierz **wprowadzenie do kompilowania aplikacji WPF (Visual C#)** lub **wprowadzenie do kompilowania aplikacji WPF (Visual Basic)**.  
  
5. Wybierz **Pobierz** przycisk, a następnie wybierz **Zamknij** przycisku.  
  
   Wprowadzenie do próbki kompilowania aplikacji WPF pojawia się w **nowy projekt** okno dialogowe.  
  
#### <a name="to-create-a-solution-for-the-sample-application"></a>Aby utworzyć rozwiązanie dla przykładowej aplikacji  
  
1.  Otwórz **nowy projekt** okno dialogowe.  
  
     ![Na pasku menu wybierz kolejno opcje Plik, nowe, projektów](../ide/media/exploreide-filenewproject.png "ExploreIDE FileNewProject")  
  
2.  W **zainstalowane** kategorii, wybierz **przykłady** kategorię, aby wyświetlić wprowadzenie do próbki kompilowania aplikacji WPF.  
  
3.  Nazwij rozwiązanie `IntroWPFcsharp` dla języka Visual C#.  
  
     ![Dialogowego Nowy projekt, zainstalowane przykłady](../ide/media/buildwalk-newprojectdlgintrotowpfsample.png "BuildWalk_NewProjectdlgIntrotoWPFsample")  
  
     LUB  
  
     Nazwij rozwiązanie `IntroWPFvb` dla języka Visual Basic.  
  
     ![Dialogowego Nowy projekt, Visual Basic przykładowy](../ide/media/buildwalk-newprojectdlgintrotowpfsamplevb.png "BuildWalk_NewProjectdlgIntrotoWPFsampleVB")  
  
4.  Wybierz **OK** przycisku.  
  
##  <a name="BKMK_CreateBuildConfig"></a> Utwórz niestandardową konfigurację kompilacji  
 Podczas tworzenia rozwiązania Debuguj i zwolnij konfiguracje kompilacji i ich domyślne elementy docelowe platformy są automatycznie definiowane dla rozwiązania. Następnie można dostosować te konfiguracje lub tworzyć własne. Konfiguracje kompilacji określają typ kompilacji. Platformy kompilacji określają system operacyjny do aplikacji jest przeznaczony dla tej konfiguracji. Aby uzyskać więcej informacji, zobacz [ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md), [ogólne informacje o platformach kompilacji](../ide/understanding-build-platforms.md), i [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 Można zmienić lub utworzyć konfigurację i ustawienia platformy za pomocą **programu Configuration Manager** okno dialogowe. W tej procedurze utworzysz konfigurację kompilacji dla badania.  
  
#### <a name="to-create-a-build-configuration"></a>Aby utworzyć konfigurację kompilacji  
  
1. Otwórz **programu Configuration Manager** okno dialogowe.  
  
    ![Tworzenie programu Configuration Manager polecenie menu](../ide/media/buildwalk-configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  
  
2. W **Konfiguracja rozwiązania aktywnego** wybierz **New**.  
  
3. W **nowa konfiguracja rozwiązania** dialogowym i nazwij nową konfigurację `Test`, skopiuj ustawienia z istniejącej konfiguracji programu debugowania, a następnie wybierz **OK** przycisku.  
  
    ![Nowe okno dialogowe konfiguracji rozwiązania](../ide/media/buildwalk-newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  
  
4. W **aktywną platformą rozwiązania** wybierz **New**.  
  
5. W **nowa platforma rozwiązania** okna dialogowego wybierz **x64**i nie Kopiuj ustawień z x86 platformy.  
  
    ![Okno dialogowe Nowy platformy rozwiązania](../ide/media/buildwalk-newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  
  
6. Wybierz **OK** przycisku.  
  
   Konfiguracja rozwiązania aktywnego został zmieniony na Test z aktywną platformą rozwiązania ustawiony na x64.  
  
   ![Program Configuration Manager z konfiguracji testu](../ide/media/buildwalk-configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  
  
   Można szybko sprawdzić lub zmienić konfigurację aktywngo rozwiązania, używając **konfiguracje rozwiązania** listy na **standardowa** paska narzędzi.  
  
   ![Opcja konfiguracji rozwiązania standardowy pasek narzędzi](../ide/media/buildwalk-standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
##  <a name="BKMK_building"></a> Kompiluj aplikację  
 Następnie Skompiluj rozwiązanie za pomocą konfiguracji niestandardowej kompilacji.  
  
#### <a name="to-build-the-solution"></a>Aby skompilować rozwiązanie  
  
- Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
  **Dane wyjściowe** okno wyświetla wyniki kompilacji. Kompilacja powiodła się, ale zostały wygenerowane komunikaty ostrzegawcze.  
  
  Rysunek 1: Ostrzeżenia Visual Basic  
  
  ![Dane wyjściowe okna języka Visual Basic](../ide/media/buildwalk-vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")  
  
  Rysunek 2: Wizualne C# ostrzeżenia  
  
  ![Output Window Visual C&#35;](../ide/media/buildwalk-csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")  
  
##  <a name="BKMK_hidewarning"></a> Ukryj ostrzeżenia kompilatora  
 Można tymczasowo ukryć niektóre komunikaty ostrzegawcze podczas kompilacji zamiast je zaśmiecać dane wyjściowe kompilacji.  
  
#### <a name="to-hide-a-specific-visual-c-warning"></a>Aby ukryć szczególne ostrzeżenie programu Visual C#  
  
1.  W **Eksploratora rozwiązań**, wybierz węzeł najwyższego poziomu projektu.  
  
2.  Na pasku menu wybierz **widoku**, **stron właściwości**.  
  
     **Projektanta projektu** zostanie otwarty.  
  
3.  Wybierz **kompilacji** strony i następnie **pomijanie ostrzeżeń** Określ numer ostrzeżenia `1762`.  
  
     ![Build page, Project Designer](../ide/media/buildwalk-csharpsuppresswarnings.png "BuildWalk_CsharpSuppressWarnings")  
  
     Aby uzyskać więcej informacji, zobacz [Stroka kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
4.  Skompiluj rozwiązanie.  
  
     **Dane wyjściowe** okna wyświetla tylko informacje podsumowujące dla kompilacji.  
  
     ![Okno danych wyjściowych, Visual C&#35; ostrzeżenia](../ide/media/buildwalk-visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
#### <a name="to-suppress-all-visual-basic-build-warnings"></a>Aby pominąć wszystkie ostrzeżenia kompilacji programu Visual Basic  
  
1. W **Eksploratora rozwiązań**, wybierz węzeł najwyższego poziomu projektu.  
  
2. Na pasku menu wybierz **widoku**, **stron właściwości**.  
  
    **Projektanta projektu** zostanie otwarty.  
  
3. Na **skompilować** wybierz opcję **Wyłącz wszystkie ostrzeżenia** pole wyboru.  
  
    ![Strona kompilowania, Projektant projektu](../ide/media/buildwalk-vbsuppresswarnings.png "BuildWalk_VBSuppressWarnings")  
  
    Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
4. Skompiluj rozwiązanie.  
  
   **Dane wyjściowe** okna wyświetla tylko informacje podsumowujące dla kompilacji.  
  
   ![Okno danych wyjściowych, Visual Basic kompilacji ostrzeżenia](../ide/media/buildwalk-visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
   Aby uzyskać więcej informacji, zobacz [jak: Pomijanie ostrzeżeń kompilatora](../ide/how-to-suppress-compiler-warnings.md).  
  
##  <a name="BKMK_outputdetails"></a> Wyświetl dodatkowe szczegóły kompilacji w oknie danych wyjściowych  
 Możesz zmienić ilość informacji dotyczących procesu kompilacji, który pojawia się w **dane wyjściowe** okna. Poziom szczegółowości jest zazwyczaj ustawiony na minimalny, co oznacza, że **dane wyjściowe** okna wyświetla tylko podsumowanie procesu kompilacji wraz z wysokim priorytetem ostrzeżeń i błędów. Więcej informacji na temat kompilacji można wyświetlić przy użyciu [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchomienia](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).  
  
> [!IMPORTANT]
>  Jeśli wyświetlisz więcej informacji, kompilacja potrwa dłużej.  
  
#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Aby zmienić ilość informacji w oknie danych wyjściowych  
  
1. Otwórz **opcje** okno dialogowe.  
  
    ![Opcje polecenia w menu narzędzia](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE ToolsOptionsmenu")  
  
2. Wybierz **projekty i rozwiązania** kategorii, a następnie wybierz **kompilowanie i uruchamianie** strony.  
  
3. W **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** wybierz **normalny**, a następnie wybierz **OK** przycisku.  
  
4. Na pasku menu wybierz **kompilacji**, **czyste rozwiązanie**.  
  
5. Skompiluj rozwiązanie, a następnie zapoznaj się z informacjami w **dane wyjściowe** okna.  
  
    Informacja o kompilacji obejmuje czas rozpoczęcia kompilacji (umieszczony na początku), kolejność, w której pliki zostały przetworzone i ilość czasu trwania procesu do ukończenia (znajdujący się na końcu). Informacje te obejmują także składnię rzeczywistą kompilatora działającą w programie Visual Studio podczas kompilacji.  
  
    Na przykład w kompilacji Visual C# [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) opcji wyświetla kod ostrzegawczy 1762, który określono wcześniej w tym temacie, oraz trzy inne ostrzeżenia.  
  
    W kompilacji Visual Basic [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) nie zawiera określonych ostrzeżeń do wykluczenia, więc żadne ostrzeżenia nie są wyświetlane.  
  
   > [!TIP]
   >  Możesz przeszukiwać zawartość **dane wyjściowe** okno po wyświetleniu **znaleźć** okno dialogowe, wybierając klawisze Ctrl + F.  
  
   Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
##  <a name="BKMK_releasebuild"></a> Tworzenie kompilacji wydania  
 Można utworzyć wersję przykładowej aplikacji, która jest zoptymalizowana do wysłania go. W przypadku kompilacji wydania określisz, że plik wykonywalny jest kopiowany do udziału sieciowego, zanim rozpocznie się kompilowanie.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Zmiana katalogu wyjściowego kompilacji](../ide/how-to-change-the-build-output-directory.md) i [kompilowanie oraz Oczyszczanie projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).  
  
#### <a name="to-specify-a-release-build-for-visual-basic"></a>Aby określić kompilację wydania dla języka Visual Basic  
  
1.  Otwórz **Projektant projektu**.  
  
     ![Menu Widok, polecenie strony właściwości](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2.  Wybierz **skompilować** strony.  
  
3.  W **konfiguracji** wybierz **wersji**.  
  
4.  W **platformy** wybierz **x86**.  
  
5.  W **ścieżkę wyjściową kompilacji** Określ ścieżkę sieciową.  
  
     Na przykład można określić \\\myserver\builds.  
  
    > [!IMPORTANT]
    >  Okno komunikatu może pojawić się ostrzeżenie, że udział sieciowy, który został określony może nie być zaufaną lokalizacją. Jeśli masz zaufanie do lokalizacji, która została określona, wybierz opcję **OK** przycisk w oknie komunikatu.  
  
6.  Skompiluj aplikację.  
  
     ![Kompiluj rozwiązanie, polecenie w menu kompilacja](../ide/media/exploreide-buildsolution.png "Skompiluj rozwiązanie ExploreIDE")  
  
#### <a name="to-specify-a-release-build-for-visual-c"></a>Aby określić kompilację wydania dla języka Visual C#  
  
1. Otwórz **Projektant projektu**.  
  
    ![Menu Widok, polecenie strony właściwości](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2. Wybierz **kompilacji** strony.  
  
3. W **konfiguracji** wybierz **wersji**.  
  
4. W **platformy** wybierz **x86**.  
  
5. W **ścieżkę wyjściową** Określ ścieżkę sieciową.  
  
    Na przykład można określić \\\myserver\builds.  
  
   > [!IMPORTANT]
   >  Okno komunikatu może pojawić się ostrzeżenie, że udział sieciowy, który został określony może nie być zaufaną lokalizacją. Jeśli masz zaufanie do lokalizacji, która została określona, wybierz opcję **OK** przycisk w oknie komunikatu.  
  
6. Skompiluj aplikację.  
  
    ![Kompiluj rozwiązanie, polecenie w menu kompilacja](../ide/media/exploreide-buildsolution.png "Skompiluj rozwiązanie ExploreIDE")  
  
   Plik wykonywalny jest kopiowany do określonej ścieżki sieciowej. Jego ścieżka byłaby \\\myserver\builds\\*FileName*.exe.  
  
   Gratulacje: zakończyła się pomyślnie w tym przewodniku.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie projektu (C++)](http://msdn.microsoft.com/library/d459bc03-88ef-48d0-9f9a-82d17f0b6a4d)   
 [Omówienie wstępnej kompilacji projektu aplikacji sieci Web platformy ASP.NET](http://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)   
 [Przewodnik: Korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md)
