---
title: 'Przewodnik: kompilowanie aplikacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f96909d3051e18fe3992e68b44b2948d1e23ebd6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670120"
---
# <a name="walkthrough-building-an-application"></a>Wskazówki: kompilowanie aplikacji

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zakończeniu tego instruktażu zobaczysz więcej opcji, które można skonfigurować podczas kompilowania aplikacji za pomocą programu Visual Studio. Należy utworzyć niestandardową konfigurację kompilacji, ukryć niektóre komunikaty ostrzegawcze i zwiększyć informacje wyjściowe kompilacji, między innymi zadaniami, dla przykładowej aplikacji.

Ten temat zawiera następujące sekcje:

[Instalowanie przykładowej aplikacji](../ide/walkthrough-building-an-application.md#BKMK_installapp)

[Utwórz niestandardową konfigurację kompilacji](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)

[Kompilowanie aplikacji](../ide/walkthrough-building-an-application.md#BKMK_building)

[Ukryj ostrzeżenia kompilatora](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)

[Wyświetl dodatkowe szczegóły kompilacji w Okno Dane wyjściowe](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)

[Utwórz kompilację wydania](../ide/walkthrough-building-an-application.md#BKMK_releasebuild)

## <a name="BKMK_installapp"></a>Instalowanie przykładowej aplikacji

Użyjesz okna dialogowego **rozszerzenia i aktualizacje** , aby znaleźć i zainstalować [wprowadzenie do kompilowania aplikacji WPF](http://code.msdn.microsoft.com/Introduction-to-Building-b8d16419?SRC=VSIDE) przykład z galerii przykładów w witrynie sieci Web firmy Microsoft. Galeria przykładów zawiera różne przykładowe projekty i kod, które można pobrać i przejrzeć podczas planowania i opracowywania aplikacji.

#### <a name="to-install-the-sample-application"></a>Aby zainstalować przykładową aplikację

1. Na pasku menu wybierz **Narzędzia**, **rozszerzenia i aktualizacje**.

2. Wybierz kategorię **online** , a następnie wybierz kategorię **Galeria przykładów** .

3. Określ `Introduction` w polu wyszukiwania, aby znaleźć przykład.

    ![Okno dialogowe rozszerzenia i aktualizacje](../ide/media/buildwalk-extensionsdialogsampledownload.png "BuildWalk_ExtensionsDialogSampleDownload")

4. Na liście wyników wybierz opcję **wprowadzenie do kompilowania aplikacji WPF (wizualizacji C#)** lub **wprowadzenie do kompilowania aplikacji WPF (Visual Basic)** .

5. Wybierz przycisk **Pobierz** , a następnie wybierz przycisk **Zamknij** .

   Przykład wprowadzenia do kompilowania aplikacji WPF pojawia się w oknie dialogowym **Nowy projekt** .

#### <a name="to-create-a-solution-for-the-sample-application"></a>Aby utworzyć rozwiązanie dla przykładowej aplikacji

1. Otwórz okno dialogowe **Nowy projekt** .

     ![Na pasku menu wybierz kolejno opcje plik, nowy, projekt.](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. W **zainstalowanej** kategorii wybierz kategorię **przykłady** , aby wyświetlić wprowadzenie do kompilowania przykładowych aplikacji WPF.

3. Nazwij rozwiązanie `IntroWPFcsharp` dla wizualizacji C#.

     ![Nowy projekt, okno dialogowe, zainstalowane przykłady](../ide/media/buildwalk-newprojectdlgintrotowpfsample.png "BuildWalk_NewProjectdlgIntrotoWPFsample")

     LUB

     Nadaj nazwę `IntroWPFvb` rozwiązanie Visual Basic.

     ![Okno dialogowe Nowy projekt, Visual Basic przykład](../ide/media/buildwalk-newprojectdlgintrotowpfsamplevb.png "BuildWalk_NewProjectdlgIntrotoWPFsampleVB")

4. Wybierz przycisk **OK** .

## <a name="BKMK_CreateBuildConfig"></a>Utwórz niestandardową konfigurację kompilacji

Podczas tworzenia rozwiązania, debugowanie i wydanie konfiguracji kompilacji oraz ich domyślne obiekty docelowe platformy są definiowane automatycznie dla rozwiązania. Następnie można dostosować te konfiguracje lub utworzyć własne. Konfiguracje kompilacji określają typ kompilacji. Platformy kompilacji określają system operacyjny, dla którego aplikacja jest przeznaczona dla danej konfiguracji. Aby uzyskać więcej informacji, zobacz [Omówienie konfiguracji kompilacji](../ide/understanding-build-configurations.md), [zrozumienie platform kompilacji](../ide/understanding-build-platforms.md)oraz [konfiguracje debugowania i wydania projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

Ustawienia konfiguracji i platformy można zmienić lub utworzyć przy użyciu okna dialogowego **Configuration Manager** . W tej procedurze utworzysz konfigurację kompilacji na potrzeby testowania.

#### <a name="to-create-a-build-configuration"></a>Aby utworzyć konfigurację kompilacji

1. Otwórz okno dialogowe **Configuration Manager** .

    ![Menu Kompilacja, Configuration Manager polecenie](../ide/media/buildwalk-configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")

2. Na liście **Konfiguracja rozwiązania aktywnego** wybierz pozycję **Nowy**.

3. W oknie dialogowym **Nowa konfiguracja rozwiązania** Nazwij nową konfigurację `Test`, skopiuj ustawienia z istniejącej konfiguracji debugowania, a następnie wybierz przycisk **OK** .

    ![Okno dialogowe Nowa konfiguracja rozwiązania](../ide/media/buildwalk-newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")

4. Na liście **aktywna Platforma rozwiązań** wybierz pozycję **Nowy**.

5. W oknie dialogowym **Nowa platforma rozwiązania** wybierz pozycję **x64**i nie Kopiuj ustawień z platformy x86.

    ![Okno dialogowe Nowa platforma rozwiązania](../ide/media/buildwalk-newsolutionplatform.png "BuildWalk_NewSolutionPlatform")

6. Wybierz przycisk **OK** .

   Aktywna Konfiguracja rozwiązania została zmieniona na test z aktywną platformą rozwiązania ustawioną na x64.

   ![Configuration Manager z konfiguracją testu](../ide/media/buildwalk-configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")

   Możesz szybko sprawdzić lub zmienić aktywną konfigurację rozwiązania, korzystając z listy **konfiguracje rozwiązania** na pasku narzędzi **Standardowy** .

   ![Opcja konfiguracji rozwiązania standardowy pasek narzędzi](../ide/media/buildwalk-standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")

## <a name="BKMK_building"></a>Kompilowanie aplikacji

Następnie można skompilować rozwiązanie przy użyciu konfiguracji kompilacji niestandardowej.

#### <a name="to-build-the-solution"></a>Aby skompilować rozwiązanie

- Na pasku menu wybierz **kompilacja**, **Kompiluj rozwiązanie**.

  W oknie **danych wyjściowych** zostaną wyświetlone wyniki kompilacji. Kompilacja powiodła się, ale Wygenerowano kilka komunikatów ostrzegawczych.

  Rysunek 1. Visual Basic ostrzeżenia

  ![Okno Dane wyjściowe Visual Basic](../ide/media/buildwalk-vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")

  Rysunek 2. ostrzeżenia C# wizualne

  ![Okno Dane wyjściowe Visual C&#35;](../ide/media/buildwalk-csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")

## <a name="BKMK_hidewarning"></a>Ukryj ostrzeżenia kompilatora

Można tymczasowo ukryć niektóre komunikaty ostrzegawcze podczas kompilacji, a nie mają one zapełniać danych wyjściowych kompilacji.

#### <a name="to-hide-a-specific-visual-c-warning"></a>Aby ukryć określone ostrzeżenie wizualizacji C#

1. W **Eksplorator rozwiązań**wybierz węzeł najwyższego poziomu projektu.

2. Na pasku menu wybierz **Widok**, **strony właściwości**.

     Zostanie otwarty **Projektant projektu** .

3. Wybierz stronę **kompilacja** , a następnie w polu **Pomiń ostrzeżenia** określ numer ostrzegawczy `1762`.

     ![Strona kompilacja, Projektant projektu](../ide/media/buildwalk-csharpsuppresswarnings.png "BuildWalk_CsharpSuppressWarnings")

     Aby uzyskać więcej informacji, zobacz [stronę Kompilacja, Projektant projektuC#()](../ide/reference/build-page-project-designer-csharp.md).

4. Skompiluj rozwiązanie.

     W oknie **dane wyjściowe** są wyświetlane tylko podsumowania kompilacji.

     ![Okno Dane wyjściowe, ostrzeżenia kompilacji&#35; Visual C](../ide/media/buildwalk-visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")

#### <a name="to-suppress-all-visual-basic-build-warnings"></a>Aby pominąć wszystkie ostrzeżenia kompilacji Visual Basic

1. W **Eksplorator rozwiązań**wybierz węzeł najwyższego poziomu projektu.

2. Na pasku menu wybierz **Widok**, **strony właściwości**.

    Zostanie otwarty **Projektant projektu** .

3. Na stronie **kompilacja** zaznacz pole wyboru **Wyłącz wszystkie ostrzeżenia** .

    ![Strona kompilowania, Projektant projektu](../ide/media/buildwalk-vbsuppresswarnings.png "BuildWalk_VBSuppressWarnings")

    Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Skompiluj rozwiązanie.

   W oknie **dane wyjściowe** są wyświetlane tylko podsumowania kompilacji.

   ![Okno Dane wyjściowe, Visual Basic ostrzeżeń kompilacji](../ide/media/buildwalk-visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")

   Aby uzyskać więcej informacji, zobacz [How to: pomijanie ostrzeżeń kompilatora](../ide/how-to-suppress-compiler-warnings.md).

## <a name="BKMK_outputdetails"></a>Wyświetl dodatkowe szczegóły kompilacji w Okno Dane wyjściowe

W oknie **dane wyjściowe** można zmienić ilość informacji o procesie kompilacji. Poziom szczegółowości kompilacji jest zwykle ustawiony na wartość minimalną, co oznacza, że okno **danych wyjściowych** wyświetla tylko podsumowanie procesu kompilacji wraz z ostrzeżeniami lub błędami o wysokim priorytecie. Więcej informacji na temat kompilacji można wyświetlić za pomocą [okna dialogowego Opcje, projektów i rozwiązań, kompilowania i uruchamiania](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Jeśli wyświetli się więcej informacji, kompilacja zajmie więcej czasu.

#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Aby zmienić ilość informacji w oknie danych wyjściowych

1. Otwórz okno dialogowe **Opcje** .

    ![Opcje polecenie w menu Narzędzia](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")

2. Wybierz kategorię **projekty i rozwiązania** , a następnie wybierz stronę **kompilacja i uruchomienie** .

3. Na liście **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** wybierz pozycję **normalne**, a następnie wybierz przycisk **OK** .

4. Na pasku menu wybierz **kompilacja**, **Wyczyść rozwiązanie**.

5. Skompiluj rozwiązanie, a następnie przejrzyj informacje w oknie **danych wyjściowych** .

    Informacje o kompilacji obejmują czas rozpoczęcia kompilacji (znajdujący się na początku), kolejność, w której pliki zostały przetworzone, oraz czas trwania procesu (znajdującego się na końcu). Te informacje obejmują również rzeczywistą składnię kompilatora, którą program Visual Studio uruchamia podczas kompilacji.

    Na przykład w kompilacji wizualnej C# opcja [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) wyświetla kod ostrzegawczy 1762, określony wcześniej w tym temacie, wraz z trzema innymi ostrzeżeniami.

    W kompilacji Visual Basic [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) nie zawiera określonych ostrzeżeń do wykluczenia, więc nie są wyświetlane żadne ostrzeżenia.

   > [!TIP]
   > Możesz przeszukać zawartość okna **danych wyjściowych** , jeśli zostanie wyświetlone okno dialogowe **Znajdź** , wybierając klawisze CTRL + F.

   Aby uzyskać więcej informacji, zobacz [jak: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="BKMK_releasebuild"></a>Utwórz kompilację wydania

Możesz utworzyć wersję przykładowej aplikacji, która została zoptymalizowana pod kątem wysyłania. W przypadku kompilacji wydania należy określić, że plik wykonywalny jest kopiowany do udziału sieciowego przed rozpoczęciem kompilacji.

Aby uzyskać więcej informacji, zobacz [How to: zmiana katalogu wyjściowego kompilacji](../ide/how-to-change-the-build-output-directory.md) i [Kompilowanie i czyszczenie projektów oraz rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

#### <a name="to-specify-a-release-build-for-visual-basic"></a>Aby określić kompilację wydania dla Visual Basic

1. Otwórz **projektanta projektu**.

     ![Menu Widok, polecenie strony właściwości](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. Wybierz stronę **kompilacja** .

3. Na liście **Konfiguracja** wybierz pozycję **Zwolnij**.

4. Na liście **platforma** wybierz pozycję **x86**.

5. W polu **Ścieżka wyjściowa kompilacji** określ ścieżkę sieciową.

     Na przykład można określić \\ \myserver\builds.

    > [!IMPORTANT]
    > Może pojawić się okno komunikatu z ostrzeżeniem, że określony udział sieciowy może nie być zaufaną lokalizacją. Jeśli ufasz określonej lokalizacji, wybierz przycisk **OK** w oknie komunikatu.

6. Skompiluj aplikację.

     ![Kompiluj polecenie rozwiązania w menu Kompilacja](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

#### <a name="to-specify-a-release-build-for-visual-c"></a>Aby określić kompilację wydania dla Visual C \#

1. Otwórz **projektanta projektu**.

    ![Menu Widok, polecenie strony właściwości](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. Wybierz stronę **kompilacja** .

3. Na liście **Konfiguracja** wybierz pozycję **Zwolnij**.

4. Na liście **platforma** wybierz pozycję **x86**.

5. W polu **Ścieżka wyjściowa** określ ścieżkę sieciową.

    Na przykład można określić \\ \myserver\builds.

   > [!IMPORTANT]
   > Może pojawić się okno komunikatu z ostrzeżeniem, że określony udział sieciowy może nie być zaufaną lokalizacją. Jeśli ufasz określonej lokalizacji, wybierz przycisk **OK** w oknie komunikatu.

6. Skompiluj aplikację.

    ![Kompiluj polecenie rozwiązania w menu Kompilacja](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Plik wykonywalny jest kopiowany do określonej ścieżki sieciowej. Jego ścieżką będzie \\ \myserver\builds \\*filename*. exe.

   Gratulacje: Przewodnik został pomyślnie ukończony.

## <a name="see-also"></a>Zobacz też

- [Przewodnik: tworzenie projektu (C++)](https://msdn.microsoft.com/library/d459bc03-88ef-48d0-9f9a-82d17f0b6a4d)
- [Przegląd prekompilowania projektu aplikacji sieci Web ASP.NET](https://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)
- [Przewodnik: Używanie programu MSBuild](../msbuild/walkthrough-using-msbuild.md)
