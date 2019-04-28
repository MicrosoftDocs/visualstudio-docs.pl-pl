---
title: 'Przewodnik: kompilowanie aplikacji'
ms.date: 09/25/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7f767f254119e1f9820c72a12e2aac7b4c141f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583031"
---
# <a name="walkthrough-build-an-application"></a>Przewodnik: kompilowanie aplikacji

Przez ukończenie tego instruktażu, zapoznasz się więcej na temat kilka opcji, które można skonfigurować podczas tworzenia aplikacji za pomocą programu Visual Studio. Będzie utworzyć niestandardową konfigurację kompilacji, ukrywał niektóre komunikaty ostrzegawcze i zwiększał kompilację informacji wyjściowych przykładowej aplikacji.

## <a name="install-the-sample-application"></a>Zainstaluj przykładową aplikację.

Pobierz [wprowadzenie do tworzenia aplikacji WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) próbki. Wybierz opcję C# lub Visual Basic. Po *zip* plik został pobrany, wyodrębnij go i Otwórz *ExpenseItIntro.sln* plików przy użyciu programu Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Utwórz niestandardową konfigurację kompilacji

Podczas tworzenia rozwiązania Debuguj i zwolnij konfiguracje kompilacji i ich domyślne elementy docelowe platformy są automatycznie definiowane dla rozwiązania. Następnie można dostosować te konfiguracje lub tworzyć własne. Konfiguracje kompilacji określają typ kompilacji. Platformy kompilacji określają system operacyjny do aplikacji jest przeznaczony dla tej konfiguracji. Aby uzyskać więcej informacji, zobacz [konfiguracje kompilacji omówienie](../ide/understanding-build-configurations.md), [omówienie platformy kompilacji](../ide/understanding-build-platforms.md), i [jak: Zestaw debugowania i zwalniania konfiguracji](../debugger/how-to-set-debug-and-release-configurations.md).

Można zmienić lub utworzyć konfigurację i ustawienia platformy za pomocą **programu Configuration Manager** okno dialogowe. W tej procedurze utworzysz konfigurację kompilacji dla badania.

### <a name="create-a-build-configuration"></a>Utwórz konfigurację kompilacji

1. Otwórz **programu Configuration Manager** okno dialogowe.

   ![Tworzenie menu i poleceń programu Configuration Manager](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. W **Konfiguracja rozwiązania aktywnego** wybierz  **\<nowy... \>**.

1. W **nowa konfiguracja rozwiązania** dialogowym i nazwij nową konfigurację `Test`, skopiuj ustawienia z istniejącego **debugowania** konfiguracji, a następnie wybierz **OK**przycisku.

   ![Nowe okno dialogowe konfiguracji rozwiązania](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. W **aktywną platformą rozwiązania** wybierz  **\<nowy... \>**.

1. W **nowa platforma rozwiązania** okna dialogowego wybierz **x64**i nie Kopiuj ustawień z x86 platformy.

   ![Okno dialogowe Nowy platformy rozwiązania](../ide/media/buildwalk_newsolutionplatform.png)

1. Wybierz **OK** przycisku.

   Konfiguracja rozwiązania active została zmieniona na **testu** z aktywną platformą rozwiązania ustawiony na x64.

   ![Program Configuration Manager z konfiguracji testu](../ide/media/buildwalk_configmanagertestconfig.png)

1. Wybierz **Zamknij**.

Można szybko sprawdzić lub zmienić konfigurację aktywngo rozwiązania, używając **konfiguracje rozwiązania** listy na **standardowa** paska narzędzi.

![Opcja konfiguracji rozwiązania standardowego paska narzędzi](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Kompilowanie aplikacji

Następnie Skompiluj rozwiązanie za pomocą konfiguracji niestandardowej kompilacji.

### <a name="build-the-solution"></a>Skompiluj rozwiązanie

- Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

    **Dane wyjściowe** okno wyświetla wyniki kompilacji. Kompilacja powiodła się.

## <a name="hide-compiler-warnings"></a>Ukryj ostrzeżenia kompilatora

Następnie wprowadzimy pewne kod, który powoduje, że ostrzeżenie generowanej przez kompilator.

1. W C# otwarty projekt *ExpenseReportPage.xaml.cs* pliku. W **ExpenseReportPage** metody, Dodaj następujący kod: `int i;`.

    LUB

    W projekcie języka Visual Basic, otwórz *ExpenseReportPage.xaml.vb* pliku. W Konstruktorze niestandardowe **publicznych Sub New...** , Dodaj następujący kod: `Dim i`.

1. Skompiluj rozwiązanie.

**Dane wyjściowe** okno wyświetla wyniki kompilacji. Kompilacja powiodła się, ale zostały wygenerowane ostrzeżenia:

![Dane wyjściowe okna języka Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![Dane wyjściowe okna Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Można tymczasowo ukryć niektóre komunikaty ostrzegawcze podczas kompilacji zamiast je zaśmiecać dane wyjściowe kompilacji.

### <a name="hide-a-specific-c-warning"></a>Ukryj określonego C# ostrzeżenie

1. W **Eksploratora rozwiązań**, wybierz węzeł najwyższego poziomu projektu.

1. Na pasku menu wybierz **widoku** > **stron właściwości**.

     **Projektanta projektu** zostanie otwarty.

1. Wybierz **kompilacji** strony i następnie **pomijanie ostrzeżeń** Określ numer ostrzeżenia **0168**.

     ![Strona, Projektant projektu kompilacji](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Aby uzyskać więcej informacji, zobacz [Stroka kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Skompiluj rozwiązanie.

     **Dane wyjściowe** okna wyświetla tylko informacje podsumowujące dla kompilacji.

     ![Okno danych wyjściowych, Visual C&#35; ostrzeżenia](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Pomiń wszystkie ostrzeżenia kompilacji programu Visual Basic

1. W **Eksploratora rozwiązań**, wybierz węzeł najwyższego poziomu projektu.

2. Na pasku menu wybierz **widoku** > **stron właściwości**.

     **Projektanta projektu** zostanie otwarty.

3. Na **skompilować** wybierz opcję **Wyłącz wszystkie ostrzeżenia** pole wyboru.

     ![Strona kompilowania, Projektant projektu](../ide/media/buildwalk_vbsuppresswarnings.png)

     Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Skompiluj rozwiązanie.

   **Dane wyjściowe** okna wyświetla tylko informacje podsumowujące dla kompilacji.

   ![Okno danych wyjściowych, Visual Basic kompilacji ostrzeżenia](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Aby uzyskać więcej informacji, zobacz [jak: Pomijanie ostrzeżeń kompilatora](../ide/how-to-suppress-compiler-warnings.md).

## <a name="display-additional-build-details-in-the-output-window"></a>Wyświetl dodatkowe kompilacji szczegóły w oknie danych wyjściowych

Możesz zmienić ilość informacji dotyczących procesu kompilacji, który pojawia się w **dane wyjściowe** okna. Poziom szczegółowości jest zazwyczaj równa **minimalne**, co oznacza, że **dane wyjściowe** okna wyświetla tylko podsumowanie procesu kompilacji wraz z wysokim priorytetem ostrzeżeń i błędów. Więcej informacji na temat kompilacji można wyświetlić przy użyciu [okno dialogowe Opcje, projekty i rozwiązania, kompilowanie i uruchamianie](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Jeśli wyświetlisz więcej informacji, kompilacja potrwa dłużej.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Zmień ilość informacji w oknie danych wyjściowych

1. Otwórz **opcje** okno dialogowe.

     ![Polecenie Opcje w menu Narzędzia](../ide/media/exploreide-toolsoptionsmenu.png)

1. Wybierz **projekty i rozwiązania** kategorii, a następnie wybierz **kompilowanie i uruchamianie** strony.

1. W **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** wybierz **normalny**, a następnie wybierz **OK** przycisku.

1. Na pasku menu wybierz **kompilacji** > **czyste rozwiązanie**.

1. Skompiluj rozwiązanie, a następnie zapoznaj się z informacjami w **dane wyjściowe** okna.

     Informacja o kompilacji obejmuje czas uruchomienia kompilacji (znajdujący się na początku) i kolejność, w której pliki zostały przetworzone. Informacje te obejmują także składnię rzeczywistą kompilatora działającą w programie Visual Studio podczas kompilacji.

     Na przykład w C# kompilacji, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) opcji wyświetla kod ostrzegawczy **1762**, który określono wcześniej w tym temacie, oraz trzy inne ostrzeżenia.

     W kompilacji Visual Basic [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) nie zawiera określonych ostrzeżeń do wykluczenia, więc żadne ostrzeżenia nie są wyświetlane.

    > [!TIP]
    > Możesz przeszukiwać zawartość **dane wyjściowe** okno po wyświetleniu **znaleźć** okno dialogowe, wybierając **Ctrl**+**F** klucze.

Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Tworzenie kompilacji wydania

Można utworzyć wersję przykładowej aplikacji, która jest zoptymalizowana do wysłania go. W przypadku kompilacji wydania określisz, że plik wykonywalny jest kopiowany do udziału sieciowego, zanim rozpocznie się kompilowanie.

Aby uzyskać więcej informacji, zobacz [jak: Zmiana katalogu wyjściowego kompilacji](../ide/how-to-change-the-build-output-directory.md) i [kompilacji i wyczyść projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="specify-a-release-build-for-visual-basic"></a>Określić kompilację wydania dla języka Visual Basic

1. Otwórz **Projektant projektu**.

     ![Menu Widok polecenie strony właściwości](../ide/media/buildwalk_viewpropertypages.png)

1. Wybierz **skompilować** strony.

1. W **konfiguracji** wybierz **wersji**.

1. W **platformy** wybierz **x86**.

1. W **ścieżkę wyjściową kompilacji** Określ ścieżkę sieciową.

     Na przykład można określić `\\myserver\builds`.

    > [!IMPORTANT]
    > Okno komunikatu może pojawić się ostrzeżenie, że udział sieciowy, który został określony może nie być zaufaną lokalizacją. Jeśli masz zaufanie do lokalizacji, która została określona, wybierz opcję **OK** przycisk w oknie komunikatu.

1. Skompiluj aplikację.

     ![Kompiluj rozwiązanie, polecenie w menu kompilacja](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>Określić kompilację wydania dla języka C\#

1. Otwórz **Projektant projektu**.

     ![Menu Widok polecenie strony właściwości](../ide/media/buildwalk_viewpropertypages.png)

1. Wybierz **kompilacji** strony.

1. W **konfiguracji** wybierz **wersji**.

1. W **platformy** wybierz **x86**.

1. W **ścieżkę wyjściową** Określ ścieżkę sieciową.

     Na przykład można określić `\\myserver\builds`.

    > [!IMPORTANT]
    > Okno komunikatu może pojawić się ostrzeżenie, że udział sieciowy, który został określony może nie być zaufaną lokalizacją. Jeśli masz zaufanie do lokalizacji, która została określona, wybierz opcję **OK** przycisk w oknie komunikatu.

1. Na **standardowy pasek narzędzi**, Ustaw konfiguracje rozwiązania **wersji** i platform rozwiązania **x86**.

1. Skompiluj aplikację.

     ![Kompiluj rozwiązanie, polecenie w menu kompilacja](../ide/media/exploreide-buildsolution.png)

   Plik wykonywalny jest kopiowany do określonej ścieżki sieciowej. Jego ścieżka byłaby `\\myserver\builds\\FileName.exe`.

Gratulacje! W tym przewodniku zakończyła się pomyślnie.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie projektu (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [Omówienie wstępnej kompilacji projektu aplikacji sieci web platformy ASP.NET](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [Przewodnik: Użyj programu MSBuild](../msbuild/walkthrough-using-msbuild.md)