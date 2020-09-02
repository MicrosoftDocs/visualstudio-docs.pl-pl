---
title: Wprowadzenie do korzystania z C++
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001b394d86e56b172bb1a50c335bd8ba5bcacb15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645630"
---
# <a name="getting-started-with-c-in-visual-studio"></a>Wprowadzenie do korzystania z C++ w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zakończeniu tego instruktażu poznasz wiele narzędzi i okien dialogowych, których można użyć podczas tworzenia aplikacji w programie Visual Studio. Utworzysz prostą aplikację w stylu "Hello, World" i dowiesz się więcej na temat pracy w zintegrowanym środowisku programistycznym (IDE).

 Ten temat zawiera następujące sekcje:

 [Zaloguj się do programu Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)

 [Tworzenie prostej aplikacji](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)

 [Dodawanie kodu do aplikacji](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)

 [Debugowanie i testowanie aplikacji](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)

 [Tworzenie wersji aplikacji](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)

## <a name="sign-in-to-visual-studio"></a><a name="BKMK_Configure"></a> Zaloguj się do programu Visual Studio
 Po uruchomieniu programu Visual Studio po raz pierwszy otrzymujesz możliwość zalogowania się przy użyciu konto Microsoft, takiego jak Live lub Outlook. Logowanie umożliwia synchronizację ustawień na wszystkich urządzeniach. Aby uzyskać więcej informacji, zobacz [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md)

 Rysunek 1. środowisko IDE programu Visual Studio

 ![Środowisko IDE z zastosowanymi ustawieniami&#43;&#43; języka Visual C](../ide/media/c-ide-defaultenvironmentlayout.png "IDE_DefaultEnvironmentLayout języka c++")

 Po otwarciu programu Visual Studio można zobaczyć trzy podstawowe części środowiska IDE: okna narzędzi, menu i paski narzędzi oraz przestrzeń okna głównego. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji, z **szybkim uruchamianiem**, paskiem menu i standardowym paskiem narzędzi u góry. Centrum okna aplikacji zawiera **stronę początkową**. Po otwarciu rozwiązania lub projektu, w tym miejscu pojawiają się edytory i projektanci. Podczas opracowywania aplikacji spędzisz większość czasu w tym środkowym obszarze.

## <a name="create-a-simple-application"></a><a name="BKMK_CreateApp"></a> Tworzenie prostej aplikacji
 Podczas tworzenia aplikacji w programie Visual Studio należy najpierw utworzyć projekt i rozwiązanie. W tym przykładzie utworzysz aplikację konsolową systemu Windows.

#### <a name="to-create-a-console-app"></a>Aby utworzyć aplikację konsolową

1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.

    ![Na pasku menu wybierz kolejno opcje plik, nowy, projekt.](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. W kategorii **Visual C++** wybierz szablon **aplikacja konsoli Win32** , a następnie nadaj nazwę projektowi `GreetingsConsoleApp` .

    ![Szablon aplikacji konsolowej Win32](../ide/media/c-ide-newprojectdlg.png "IDE_NewProjectDlg języka c++")

3. Gdy zostanie wyświetlony Kreator aplikacji Win32, wybierz przycisk **Zakończ** .

    ![Kreator aplikacji konsolowej Win32](../ide/media/c-ide-win32consoleappwizard.png "IDE_Win32ConsoleAppWizard języka c++")

   Projekt i rozwiązanie GreetingsConsoleApp, z podstawowymi plikami dla aplikacji konsolowej Win32, są tworzone i automatycznie ładowane do **Eksplorator rozwiązań**. Plik GreetingsConsoleApp. cpp zostanie otwarty w edytorze kodu. Następujące elementy są wyświetlane w **Eksplorator rozwiązań**:

   Rysunek 4. elementy projektu

   ![Pliki rozwiązania w Eksplorator rozwiązań](../ide/media/c-ide-solutioncontents.png "IDE_SolutionContents języka c++")

## <a name="add-code-to-the-application"></a><a name="BKMK_AddCode"></a> Dodawanie kodu do aplikacji
 Następnie dodasz kod w celu wyświetlenia słowa "Hello" w oknie konsoli.

#### <a name="to-display-hello-in-the-console-window"></a>Aby wyświetlić "Hello" w oknie konsoli

1. W pliku GreetingsConsoleApp. cpp wprowadź pusty wiersz przed wierszem, `return 0;` a następnie wprowadź następujący kod:

    ```
    cout << "Hello\n";
    ```

     W obszarze znajduje się czerwona linia falistej `cout` . Gdy wskażesz, pojawi się komunikat o błędzie.

     ![Tekst błędu dla cout](../ide/media/c-ide-couterror.png "IDE_CoutError języka c++")

     W oknie **Lista błędów** zostanie również wyświetlony komunikat o błędzie. Możesz wyświetlić okno według, na pasku menu, wybierając **Widok**, **Lista błędów**.

     [cout](https://msdn.microsoft.com/library/d87db6c3-e4e1-4d09-9ec5-458f55018257) jest dołączany do \<iostream\> pliku nagłówkowego.

2. Aby dołączyć nagłówek iostream, wprowadź następujący kod po `#include "stdafx.h"` :

    ```
    #include \<iostream\>
    using namespace std;
    ```

     Prawdopodobnie zauważono, że pole pojawiło się po wprowadzeniu kodu, dostarczając sugestie dotyczące wprowadzonych znaków. To pole jest częścią funkcji IntelliSense języka C++, która dostarcza instrukcje kodowania, w tym informacje o klasach i elementach członkowskich interfejsu i parametrach. Można również użyć fragmentów kodu, które są wstępnie zdefiniowanymi blokami kodu. Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md) i [fragmentów kodu](../ide/code-snippets.md).

     Czerwona linia falistej w obszarze `cout` znika po naprawieniu błędu.

3. Zapisz zmiany w pliku.

     ![Kod, który naprawia błąd cout](../ide/media/c-ide-coutfix.png "IDE_CoutFix języka c++")

## <a name="debug-and-test-the-application"></a><a name="BKMK_DebugTest"></a> Debugowanie i testowanie aplikacji
 Można debugować GreetingsConsoleApp, aby zobaczyć, czy słowo "Hello" pojawia się w oknie konsoli.

#### <a name="to-debug-the-application"></a>Aby debugować aplikację

- Uruchom Debuger.

     ![Rozpocznij debugowanie polecenia w menu Debugowanie](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")

     Debuger uruchamia i uruchamia kod. Okno konsoli (oddzielne okno, które wygląda jak wiersz polecenia) pojawia się przez kilka sekund, ale szybko zamyka się, gdy debuger przestanie działać. Aby wyświetlić tekst, należy ustawić punkt przerwania, aby zatrzymać wykonywanie programu.

#### <a name="to-add-a-breakpoint"></a>Aby dodać punkt przerwania

1. Dodaj punkt przerwania z paska menu w wierszu `return 0;` . Możesz również kliknąć na lewym marginesie, aby ustawić punkt przerwania.

    ![Przełącz polecenie punktu przerwania w menu Debugowanie](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE — Togglebreakpoint —")

    Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.

2. Wybierz klawisz F5, aby rozpocząć debugowanie.

    Zostanie uruchomiony debuger i zostanie wyświetlone okno konsoli zawierające wyraz **Hello**.

    ![Tekst powitania w oknie wiersza polecenia systemu Windows](../ide/media/c-ide-hellocommandwindow.png "IDE_HelloCommandWindow języka c++")

3. Naciśnij klawisze SHIFT + F5, aby zatrzymać debugowanie.

   Aby uzyskać więcej informacji, zobacz [projekty konsoli](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a><a name="BKMK_BuildRelease"></a> Tworzenie wersji aplikacji
 Teraz, gdy masz już pewność, że wszystko działa, możesz przygotować wersję dystrybucyjną aplikacji.

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Aby wyczyścić pliki rozwiązań i zbudować wersję przeznaczoną do publikacji

1. Na pasku menu Usuń pliki pośrednie i pliki wyjściowe, które zostały utworzone podczas poprzednich kompilacji.

    ![Polecenie Oczyść rozwiązanie w menu Kompilacja](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")

2. Zmień konfigurację kompilacji dla GreetingsConsoleApp z **Debug** na **Release**.

    ![Tworzenie dystrybucyjnej wersji tej aplikacji](../ide/media/c-ide-changingbuildtorelease.png "IDE_ChangingBuildtoRelease języka c++")

3. Skompiluj rozwiązanie.

    ![Kompiluj polecenie rozwiązania w menu Kompilacja](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Gratulujemy zakończenia instruktażu! Jeśli chcesz poznać więcej przykładów, zobacz [Visual Studio Samples](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Tworzenie prostych](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [porad dotyczących wydajności](../ide/productivity-tips-for-visual-studio.md) aplikacji [przykłady programu Visual Studio](../ide/visual-studio-samples.md) [wprowadzenie do programowania w programie Visual Studio](../ide/get-started-developing-with-visual-studio.md)
