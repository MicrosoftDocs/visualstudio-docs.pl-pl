---
title: 'Przewodnik: kompilowanie aplikacji'
description: Poznasz kilka opcji, które można skonfigurować podczas kompilowania aplikacji za pomocą programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/25/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76a281b90b3dabe2b1d91c43a27ee5f9c858f96c
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136618"
---
# <a name="walkthrough-build-an-application"></a>Przewodnik: kompilowanie aplikacji

Po zakończeniu tego instruktażu zobaczysz więcej opcji, które można skonfigurować podczas kompilowania aplikacji za pomocą programu Visual Studio. Utworzysz niestandardową konfigurację kompilacji, ukryjesz pewne komunikaty ostrzegawcze i zwiększę informacje wyjściowe kompilacji dla przykładowej aplikacji.

## <a name="install-the-sample-application"></a>Instalowanie przykładowej aplikacji

Pobierz [wprowadzenie do kompilowania przykładowych aplikacji WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) . Wybierz opcję C# lub Visual Basic. Po pobraniu pliku *zip* wyodrębnij go i Otwórz plik *ExpenseItIntro. sln* przy użyciu programu Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Utwórz niestandardową konfigurację kompilacji

Podczas tworzenia rozwiązania, debugowanie i wydanie konfiguracji kompilacji oraz ich domyślne obiekty docelowe platformy są definiowane automatycznie dla rozwiązania. Następnie można dostosować te konfiguracje lub utworzyć własne. Konfiguracje kompilacji określają typ kompilacji. Platformy kompilacji określają system operacyjny, dla którego aplikacja jest przeznaczona dla danej konfiguracji. Aby uzyskać więcej informacji, zobacz [Omówienie konfiguracji kompilacji](../ide/understanding-build-configurations.md), [Opis platform kompilacji](../ide/understanding-build-platforms.md)i [instrukcje: Ustawianie konfiguracji debugowania i wersji](../debugger/how-to-set-debug-and-release-configurations.md).

Ustawienia konfiguracji i platformy można zmienić lub utworzyć przy użyciu okna dialogowego **Configuration Manager** . W tej procedurze utworzysz konfigurację kompilacji na potrzeby testowania.

### <a name="create-a-build-configuration"></a>Utwórz konfigurację kompilacji

1. Otwórz okno dialogowe **Configuration Manager** .

   ![Menu Kompilacja, Configuration Manager polecenie](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. Na liście **Konfiguracja aktywnego rozwiązania** wybierz opcję **\<New...\>** .

1. W oknie dialogowym **Nowa konfiguracja rozwiązania** Nazwij nową konfigurację `Test` , skopiuj ustawienia z istniejącej konfiguracji **debugowania** , a następnie wybierz przycisk **OK** .

   ![Okno dialogowe Nowa konfiguracja rozwiązania](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. Na liście **aktywna Platforma rozwiązań** wybierz opcję **\<New...\>** .

1. W oknie dialogowym **Nowa platforma rozwiązania** wybierz pozycję **x64**i nie Kopiuj ustawień z platformy x86.

   ![Okno dialogowe Nowa platforma rozwiązania](../ide/media/buildwalk_newsolutionplatform.png)

1. Wybierz przycisk **OK** .

   Aktywna Konfiguracja rozwiązania została zmieniona na **test** z aktywną platformą rozwiązania ustawioną na x64.

   ![Configuration Manager z konfiguracją testu](../ide/media/buildwalk_configmanagertestconfig.png)

1. Wybierz pozycję **Zamknij**.

Możesz szybko sprawdzić lub zmienić aktywną konfigurację rozwiązania, korzystając z listy **konfiguracje rozwiązania** na pasku narzędzi **Standardowy** .

![Opcja konfiguracji rozwiązania standardowy pasek narzędzi](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Kompilowanie aplikacji

Następnie można skompilować rozwiązanie przy użyciu konfiguracji kompilacji niestandardowej.

### <a name="build-the-solution"></a>Kompilowanie rozwiązania

- Na pasku menu wybierz opcję **Kompiluj**  >  **kompilację rozwiązania**lub naciśnij **klawisze CTRL** + **SHIFT** + **B**.

    W oknie **danych wyjściowych** zostaną wyświetlone wyniki kompilacji. Kompilacja powiodła się.

## <a name="hide-compiler-warnings"></a>Ukryj ostrzeżenia kompilatora

Następnie wprowadzimy kod, który powoduje wygenerowanie ostrzeżenia przez kompilator.

1. W projekcie C# Otwórz plik *ExpenseReportPage.XAML.cs* . W metodzie **ExpenseReportPage** Dodaj następujący kod: `int i;` .

    LUB

    W projekcie Visual Basic Otwórz plik *ExpenseReportPage. XAML. vb* . W publicznym konstruktorze niestandardowym **Sub New...**, Dodaj następujący kod: `Dim i` .

1. Skompiluj rozwiązanie.

W oknie **danych wyjściowych** zostaną wyświetlone wyniki kompilacji. Kompilacja zakończyła się pomyślnie, ale wystąpiły ostrzeżenia:

![Okno Dane wyjściowe Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![&#35; Okno Dane wyjściowe Visual C](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Można tymczasowo ukryć niektóre komunikaty ostrzegawcze podczas kompilacji, a nie mają one zapełniać danych wyjściowych kompilacji.

### <a name="hide-a-specific-c-warning"></a>Ukryj określone ostrzeżenie języka C#

1. W **Eksplorator rozwiązań**wybierz węzeł najwyższego poziomu projektu.

1. Na pasku menu wybierz polecenie **Wyświetl**  >  **strony właściwości**.

     Zostanie otwarty **Projektant projektu** .

1. Wybierz stronę **kompilacja** , a następnie w polu **Pomiń ostrzeżenia** określ numer ostrzegawczy **0168**.

     ![Strona kompilacja, Projektant projektu](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Aby uzyskać więcej informacji, zobacz [stronę Kompilacja, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Skompiluj rozwiązanie.

     W oknie **dane wyjściowe** są wyświetlane tylko podsumowania kompilacji.

     ![Okno Dane wyjściowe, Visual C&#35; ostrzeżenia kompilacji](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Pomiń wszystkie ostrzeżenia kompilacji Visual Basic

1. W **Eksplorator rozwiązań**wybierz węzeł najwyższego poziomu projektu.

2. Na pasku menu wybierz polecenie **Wyświetl**  >  **strony właściwości**.

     Zostanie otwarty **Projektant projektu** .

3. Na stronie **kompilacja** zaznacz pole wyboru **Wyłącz wszystkie ostrzeżenia** .

     ![Strona kompilowania, Projektant projektu](../ide/media/buildwalk_vbsuppresswarnings.png)

     Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Skompiluj rozwiązanie.

   W oknie **dane wyjściowe** są wyświetlane tylko podsumowania kompilacji.

   ![Okno Dane wyjściowe, Visual Basic ostrzeżeń kompilacji](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Aby uzyskać więcej informacji, zobacz [How to: pomijanie ostrzeżeń kompilatora](../ide/how-to-suppress-compiler-warnings.md).

## <a name="display-additional-build-details-in-the-output-window"></a>Wyświetl dodatkowe szczegóły kompilacji w oknie danych wyjściowych

W oknie **dane wyjściowe** można zmienić ilość informacji o procesie kompilacji. Poziom szczegółowości kompilacji jest zwykle ustawiony na wartość **minimalną**, co oznacza, że okno **danych wyjściowych** wyświetla tylko podsumowanie procesu kompilacji wraz z ostrzeżeniami lub błędami o wysokim priorytecie. Więcej informacji na temat kompilacji można wyświetlić za pomocą [okna dialogowego Opcje, projektów i rozwiązań, kompilowania i uruchamiania](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Jeśli wyświetli się więcej informacji, kompilacja zajmie więcej czasu.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Zmiana ilości informacji w oknie danych wyjściowych

1. Otwórz okno dialogowe **Opcje** .

     ![Opcje polecenie w menu Narzędzia](../ide/media/exploreide-toolsoptionsmenu.png)

1. Wybierz kategorię **projekty i rozwiązania** , a następnie wybierz stronę **kompilacja i uruchomienie** .

1. Na liście **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** wybierz pozycję **normalne**, a następnie wybierz przycisk **OK** .

1. Na pasku menu wybierz kolejno opcje **Kompiluj**  >  **czyste rozwiązanie**.

1. Skompiluj rozwiązanie, a następnie przejrzyj informacje w oknie **danych wyjściowych** .

     Informacje o kompilacji obejmują czas rozpoczęcia kompilacji (znajdujący się na początku) oraz kolejność przetwarzania plików. Te informacje obejmują również rzeczywistą składnię kompilatora, którą program Visual Studio uruchamia podczas kompilacji.

     Na przykład w kompilacji C# opcja [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) wyświetla kod ostrzegawczy, **0168**, określony wcześniej w tym temacie, wraz z trzema innymi ostrzeżeniami.

     W kompilacji Visual Basic [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) nie zawiera określonych ostrzeżeń do wykluczenia, więc nie są wyświetlane żadne ostrzeżenia.

    > [!TIP]
    > Możesz przeszukać zawartość okna **danych wyjściowych** , jeśli zostanie wyświetlone okno dialogowe **Znajdź** , wybierając klawisze **Ctrl** + **F** .

Aby uzyskać więcej informacji, zobacz [jak: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Tworzenie kompilacji wydania

Możesz utworzyć wersję przykładowej aplikacji, która została zoptymalizowana pod kątem wysyłania. W przypadku kompilacji wydania należy określić, że plik wykonywalny jest kopiowany do udziału sieciowego przed rozpoczęciem kompilacji.

Aby uzyskać więcej informacji, zobacz [How to: zmiana katalogu wyjściowego kompilacji](../ide/how-to-change-the-build-output-directory.md) i [Kompilowanie i czyszczenie projektów oraz rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="specify-a-release-build-for-visual-basic"></a>Określ kompilację wydania dla Visual Basic

1. Otwórz **projektanta projektu**.

     ![Menu Widok, polecenie strony właściwości](../ide/media/buildwalk_viewpropertypages.png)

1. Wybierz stronę **kompilacja** .

1. Na liście **Konfiguracja** wybierz pozycję **Zwolnij**.

1. Na liście **platforma** wybierz pozycję **x86**.

1. W polu **Ścieżka wyjściowa kompilacji** określ ścieżkę sieciową.

     Na przykład można określić `\\myserver\builds` .

    > [!IMPORTANT]
    > Może pojawić się okno komunikatu z ostrzeżeniem, że określony udział sieciowy może nie być zaufaną lokalizacją. Jeśli ufasz określonej lokalizacji, wybierz przycisk **OK** w oknie komunikatu.

1. Skompiluj aplikację.

     ![Kompiluj polecenie rozwiązania w menu Kompilacja](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>Określ kompilację wydania dla języka C\#

1. Otwórz **projektanta projektu**.

     ![Menu Widok, polecenie strony właściwości](../ide/media/buildwalk_viewpropertypages.png)

1. Wybierz stronę **kompilacja** .

1. Na liście **Konfiguracja** wybierz pozycję **Zwolnij**.

1. Na liście **platforma** wybierz pozycję **x86**.

1. W polu **Ścieżka wyjściowa** określ ścieżkę sieciową.

     Na przykład można określić `\\myserver\builds` .

    > [!IMPORTANT]
    > Może pojawić się okno komunikatu z ostrzeżeniem, że określony udział sieciowy może nie być zaufaną lokalizacją. Jeśli ufasz określonej lokalizacji, wybierz przycisk **OK** w oknie komunikatu.

1. Na **standardowym pasku narzędzi**Ustaw konfiguracje rozwiązania na **wersje** i platformy rozwiązań na **x86**.

1. Skompiluj aplikację.

     ![Kompiluj polecenie rozwiązania w menu Kompilacja](../ide/media/exploreide-buildsolution.png)

   Plik wykonywalny jest kopiowany do określonej ścieżki sieciowej. Jego ścieżką będzie `\\myserver\builds\\FileName.exe` .

Gratulacje! Przewodnik został pomyślnie ukończony.

## <a name="see-also"></a>Zobacz też

- [Przewodnik: Tworzenie projektu (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [Przegląd prekompilowania projektu aplikacji sieci Web ASP.NET](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [Przewodnik: korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md)
