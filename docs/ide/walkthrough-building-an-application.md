---
title: 'Przewodnik: kompilowanie aplikacji'
ms.date: 09/25/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d94a525f9938b6845584b6d5872bd486e947025d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115399"
---
# <a name="walkthrough-build-an-application"></a>Przewodnik: kompilowanie aplikacji

Po wykonaniu tego przewodnika, można zapoznać się z kilku opcji, które można skonfigurować podczas tworzenia aplikacji za pomocą programu Visual Studio. Utworzysz niestandardową konfigurację kompilacji, ukryjesz pewne komunikaty ostrzegawcze i zwiększysz informacje wyjściowe kompilacji dla przykładowej aplikacji.

## <a name="install-the-sample-application"></a>Zainstaluj przykładową aplikację

Pobierz [wprowadzenie do tworzenia aplikacji WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) przykład. Wybierz c# lub Visual Basic. Po pobraniu pliku *zip* wyodrębnij go i otwórz plik *ExpenseItIntro.sln* za pomocą programu Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Tworzenie niestandardowej konfiguracji kompilacji

Podczas tworzenia rozwiązania, debugowania i uruchamiania konfiguracji kompilacji i ich domyślne cele platformy są definiowane dla rozwiązania automatycznie. Następnie można dostosować te konfiguracje lub utworzyć własne. Konfiguracje kompilacji określają typ kompilacji. Platformy kompilacji określić system operacyjny, który jest przeznaczony dla tej konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md), Zrozumieć platformy [kompilacji](../ide/understanding-build-platforms.md)i [Jak: Ustawianie konfiguracji debugowania i zwalniania](../debugger/how-to-set-debug-and-release-configurations.md).

Konfiguracje i ustawienia platformy można zmieniać lub tworzyć za pomocą okna dialogowego **Menedżer konfiguracji.** W tej procedurze utworzysz konfigurację kompilacji do testowania.

### <a name="create-a-build-configuration"></a>Tworzenie konfiguracji kompilacji

1. Otwórz okno **dialogowe Menedżer konfiguracji.**

   ![Menu Kompilacja, polecenie Menedżer konfiguracji](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. Na liście **Konfiguracja rozwiązania Active** wybierz pozycję ** \<Nowy... \>**.

1. W oknie dialogowym **Nowa konfiguracja** `Test`rozwiązania nazwij nową konfigurację, skopiuj ustawienia z istniejącej konfiguracji **debugowania,** a następnie wybierz przycisk **OK.**

   ![Okno dialogowe Konfiguracja nowego rozwiązania](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. Na liście **Platformy aktywnego rozwiązania** wybierz pozycję ** \<Nowy... \>**.

1. W oknie dialogowym **Nowa platforma rozwiązań** wybierz **x64**i nie kopiuj ustawień z platformy x86.

   ![Okno dialogowe Nowa platforma rozwiązań](../ide/media/buildwalk_newsolutionplatform.png)

1. Wybierz przycisk **OK.**

   Konfiguracja aktywnego rozwiązania została zmieniona na **Test** z platformą aktywnego rozwiązania ustawioną na x64.

   ![Menedżer konfiguracji z konfiguracją testu](../ide/media/buildwalk_configmanagertestconfig.png)

1. Wybierz **pozycję Zamknij**.

Konfigurację aktywnego rozwiązania można szybko zweryfikować lub zmienić za pomocą listy **Konfiguracje rozwiązania** na pasku narzędzi **Standardowy.**

![Opcja konfiguracji rozwiązania Standardowy pasek narzędzi](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Kompilowanie aplikacji

Następnie skompilujesz rozwiązanie z konfiguracją kompilacji niestandardowej.

### <a name="build-the-solution"></a>Kompilowanie rozwiązania

- Na pasku menu wybierz pozycję **Build** > **Build Solution**lub naciśnij klawisz **Ctrl**+**Shift**+**B**.

    Okno **Dane wyjściowe** wyświetla wyniki kompilacji. Kompilacja powiodła się.

## <a name="hide-compiler-warnings"></a>Ukryj ostrzeżenia kompilatora

Następnie wprowadzimy kod, który powoduje, że ostrzeżenie ma być generowane przez kompilator.

1. W projekcie C# otwórz plik *ExpenseReportPage.xaml.cs.* W **metodzie ExpenseReportPage** dodaj następujący `int i;`kod: .

    LUB

    W projekcie Visual Basic otwórz plik *ExpenseReportPage.xaml.vb.* W konstruktorze niestandardowym **Public Sub New...** dodaj następujący kod: `Dim i`.

1. Skompiluj rozwiązanie.

Okno **Dane wyjściowe** wyświetla wyniki kompilacji. Kompilacja powiodła się, ale zostały wygenerowane ostrzeżenia:

![Podstawowe okno wyjściowe](../ide/media/buildwalk_vbbuildoutputwnd.png)

![Okno wyjściowe Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Można tymczasowo ukryć niektóre komunikaty ostrzegawcze podczas kompilacji, a nie je zaśmiecać dane wyjściowe kompilacji.

### <a name="hide-a-specific-c-warning"></a>Ukrywanie określonego ostrzeżenia języka C#

1. W **Eksploratorze rozwiązań**wybierz węzeł projektu najwyższego poziomu.

1. Na pasku menu wybierz pozycję **Wyświetl** > **strony właściwości**.

     Zostanie otwarty **projektant projektu.**

1. Wybierz stronę **Kompilacja,** a następnie w polu **Pomijaj ostrzeżenia** określ numer ostrzeżenia **0168**.

     ![Strona kompilacji, Projektant projektu](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Aby uzyskać więcej informacji, zobacz [Strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Skompiluj rozwiązanie.

     W oknie **Dane wyjściowe** są wyświetlane tylko informacje podsumowujące dla kompilacji.

     ![Okno wyjściowe, wizualne C&#35; ostrzeżenia kompilacji](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Pomijanie wszystkich ostrzeżeń kompilacji języka Visual Basic

1. W **Eksploratorze rozwiązań**wybierz węzeł projektu najwyższego poziomu.

2. Na pasku menu wybierz pozycję **Wyświetl** > **strony właściwości**.

     Zostanie otwarty **projektant projektu.**

3. Na stronie **Kompilacja** zaznacz pole wyboru **Wyłącz wszystkie ostrzeżenia.**

     ![Strona kompilacji, Projektant projektu](../ide/media/buildwalk_vbsuppresswarnings.png)

     Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Skompiluj rozwiązanie.

   W oknie **Dane wyjściowe** są wyświetlane tylko informacje podsumowujące dla kompilacji.

   ![Okno danych wyjściowych, ostrzeżenia kompilacji visual basic](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Aby uzyskać więcej informacji, zobacz [Jak: Pomijanie ostrzeżeń kompilatora](../ide/how-to-suppress-compiler-warnings.md).

## <a name="display-additional-build-details-in-the-output-window"></a>Wyświetlanie dodatkowych szczegółów kompilacji w oknie Dane wyjściowe

Można zmienić, ile informacji o procesie kompilacji pojawia się w oknie **Dane wyjściowe.** Szczegółowość kompilacji jest zwykle **ustawiona**na Minimalne , co oznacza, że okno **Dane wyjściowe** wyświetla tylko podsumowanie procesu kompilacji wraz z ostrzeżeniami lub błędami o wysokim priorytecie. Więcej informacji o kompilacji można wyświetlić za pomocą [okna dialogowego Opcje, Projekty i rozwiązania, Tworzenie i uruchamianie](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Jeśli wyświetlisz więcej informacji, kompilacja potrwa dłużej.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Zmienianie ilości informacji w oknie Dane wyjściowe

1. Otwórz okno dialogowe **Opcje.**

     ![Polecenie Opcje w menu Narzędzia](../ide/media/exploreide-toolsoptionsmenu.png)

1. Wybierz kategorię **Projekty i rozwiązania,** a następnie wybierz stronę **Kompilacja i uruchamianie.**

1. Na liście **pełnej szczegółowości kompilacji kompilacji projektu MSBuild** wybierz pozycję **Normalny**, a następnie wybierz przycisk **OK.**

1. Na pasku menu wybierz pozycję **Build** > **Clean Solution**.

1. Skompiluj rozwiązanie, a następnie przejrzyj informacje w oknie **Dane wyjściowe.**

     Informacje o kompilacji obejmują czas rozpoczęcia kompilacji (znajdujący się na początku) i kolejność przetwarzania plików. Te informacje obejmują również składnię kompilatora rzeczywiste, który program Visual Studio jest uruchamiany podczas kompilacji.

     Na przykład w kompilacji Języka C# opcja [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) wyświetla kod ostrzeżenia **0168**, który został określony wcześniej w tym temacie, wraz z trzema innymi ostrzeżeniami.

     W kompilacji języka Visual Basic [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) nie zawiera określonych ostrzeżeń do wykluczenia, więc nie są wyświetlane żadne ostrzeżenia.

    > [!TIP]
    > Zawartość okna **Dane wyjściowe** można przeszukiwać, jeśli okno dialogowe **Znajdowanie** jest wyświetlane, wybierając klawisze **Ctrl**+**F.**

Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Tworzenie kompilacji wydania

Można utworzyć wersję przykładowej aplikacji, która jest zoptymalizowana pod kątem jej wysyłki. W przypadku kompilacji wydania określ, że plik wykonywalny jest kopiowany do udziału sieciowego przed rozpoczęciem kompilacji.

Aby uzyskać więcej informacji, zobacz [Jak: Zmienianie katalogu wyjściowego kompilacji](../ide/how-to-change-the-build-output-directory.md) i [kompilacji oraz czyszczenie projektów i rozwiązań w programie Visual Studio.](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)

### <a name="specify-a-release-build-for-visual-basic"></a>Określanie kompilacji wersji dla języka Visual Basic

1. Otwórz **projektanta projektu**.

     ![Menu Wyświetl, polecenie Strony właściwości](../ide/media/buildwalk_viewpropertypages.png)

1. Wybierz stronę **Kompilacja.**

1. Na liście **Konfiguracja** wybierz pozycję **Zwolnij**.

1. Na liście **Platforma** wybierz **x86**.

1. W polu **Stwórz ścieżkę wyjściową** określ ścieżkę sieciową.

     Na przykład można `\\myserver\builds`określić .

    > [!IMPORTANT]
    > Może pojawić się okno komunikatu z ostrzeżeniem, że określony udział sieciowy może nie być lokalizacją zaufaną. Jeśli ufasz określonej lokalizacji, wybierz przycisk **OK** w oknie komunikatu.

1. Skompiluj aplikację.

     ![Polecenie Kompilacja rozwiązania w menu Kompilacja](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>Określanie kompilacji wersji dla języka C\#

1. Otwórz **projektanta projektu**.

     ![Menu Wyświetl, polecenie Strony właściwości](../ide/media/buildwalk_viewpropertypages.png)

1. Wybierz stronę **Kompilacja.**

1. Na liście **Konfiguracja** wybierz pozycję **Zwolnij**.

1. Na liście **Platforma** wybierz **x86**.

1. W polu **Ścieżka wyjściowa** określ ścieżkę sieciową.

     Na przykład można `\\myserver\builds`określić .

    > [!IMPORTANT]
    > Może pojawić się okno komunikatu z ostrzeżeniem, że określony udział sieciowy może nie być lokalizacją zaufaną. Jeśli ufasz określonej lokalizacji, wybierz przycisk **OK** w oknie komunikatu.

1. Na **standardowym pasku narzędzi**ustaw konfiguracje rozwiązań na **Wydanie,** a platformy rozwiązań na **x86**.

1. Skompiluj aplikację.

     ![Polecenie Kompilacja rozwiązania w menu Kompilacja](../ide/media/exploreide-buildsolution.png)

   Plik wykonywalny jest kopiowany do określonej ścieżki sieciowej. Jego droga `\\myserver\builds\\FileName.exe`będzie .

Gratulacje! Ten przewodnik został pomyślnie ukończony.

## <a name="see-also"></a>Zobacz też

- [Instruktaż: Tworzenie projektu (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [ASP.NET przegląd wstępnej kompilacji projektu aplikacji sieci Web](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [Instruktaż: Użyj msbuild](../msbuild/walkthrough-using-msbuild.md)
