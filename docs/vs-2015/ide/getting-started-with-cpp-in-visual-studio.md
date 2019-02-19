---
title: Wprowadzenie do korzystania z C++
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 264fcea4b04b1777a455199789ed1bb9c3757f7c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54758245"
---
# <a name="getting-started-with-c-in-visual-studio"></a>Wprowadzenie do korzystania z C++ w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przez ukończenie tego instruktażu, zapoznasz się z wielu narzędzi i oknach dialogowych, używane podczas tworzenia aplikacji za pomocą programu Visual Studio. Utworzysz prostą "Hello, World"-stylów aplikacji, podczas gdy dowiesz się więcej na temat pracy w zintegrowanym środowisku programistycznym (IDE).

 Ten temat zawiera następujące sekcje:

 [Zaloguj się do programu Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)

 [Tworzenie prostej aplikacji](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)

 [Dodaj kod do aplikacji](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)

 [Debugowanie i testowanie aplikacji](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)

 [Tworzenie dystrybucyjnej wersji aplikacji](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)

##  <a name="BKMK_Configure"></a> Zaloguj się do programu Visual Studio
 Po uruchomieniu programu Visual Studio po raz pierwszy podano zyskując szansę na zalogowanie się przy użyciu konta Microsoft, takiego jak Live lub programu Outlook. Logowanie umożliwia ustawienia mają być synchronizowane na wszystkich urządzeniach. Aby uzyskać więcej informacji, zobacz [logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md)

 Rysunek 1: Visual Studio IDE

 ![Środowisko IDE z Visual C&#43; &#43; ustawienia stosowane](../ide/media/c-ide-defaultenvironmentlayout.png "IDE_DefaultEnvironmentLayout C ++")

 Po otwarciu programu Visual Studio, można wyświetlić trzy podstawowe części IDE: narzędzie systemu windows, menu i paski narzędzi oraz przestrzeń głównego okna. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji za pomocą **Szybkie uruchamianie**, pasek menu i standardowy pasek narzędzi u góry. Na środku okna aplikacji zawiera **strona startowa**. Po otwarciu rozwiązania lub projektu, w tym miejscu pojawiają się edytory i projektanty. Podczas opracowywania aplikacji spędzisz większość czasu w tym środkowym obszarze.

##  <a name="BKMK_CreateApp"></a> Tworzenie prostej aplikacji
 Podczas tworzenia aplikacji w programie Visual Studio, należy najpierw utworzyć projekt i rozwiązanie. W tym przykładzie utworzysz aplikację konsolową w języku Windows.

#### <a name="to-create-a-console-app"></a>Aby utworzyć aplikację konsoli

1. Na pasku menu wybierz **pliku**, **New**, **projektu**.

    ![Na pasku menu wybierz kolejno opcje Plik, nowe, projektów](../ide/media/exploreide-filenewproject.png "ExploreIDE FileNewProject")

2. W **Visual C++** kategorii, wybierz **Aplikacja konsoli Win32** szablonu, a następnie nazwę projektu `GreetingsConsoleApp`.

    ![Szablon Aplikacja konsoli Win32](../ide/media/c-ide-newprojectdlg.png "IDE_NewProjectDlg C ++")

3. Gdy pojawi się Kreator aplikacji Win32, wybierz **Zakończ** przycisku.

    ![Kreator aplikacji konsoli Win32](../ide/media/c-ide-win32consoleappwizard.png "IDE_Win32ConsoleAppWizard C ++")

   GreetingsConsoleApp projektu i rozwiązania przy użyciu podstawowych plików dla aplikacji konsoli Win32 są tworzone i ładowane automatycznie do **Eksploratora rozwiązań**. Plik GreetingsConsoleApp.cpp jest otwarty w edytorze kodu. Następujące elementy są wyświetlane w **Eksploratora rozwiązań**:

   Rysunek 4: Elementy projektu

   ![Pliki rozwiązania w Eksploratorze rozwiązań](../ide/media/c-ide-solutioncontents.png "IDE_SolutionContents C ++")

##  <a name="BKMK_AddCode"></a> Dodaj kod do aplikacji
 Następnie dodasz kod, aby wyświetlić słowo "Cześć" w oknie konsoli.

#### <a name="to-display-hello-in-the-console-window"></a>Aby wyświetlić "Hello" w oknie konsoli

1.  W pliku GreetingsConsoleApp.cpp, należy wprowadzić pusty wiersz przed wierszem `return 0;` a następnie wprowadź poniższy kod:

    ```
    cout << "Hello\n";
    ```

     Czerwona linia falista jest wyświetlany w obszarze `cout`. Komunikat o błędzie pojawia się po wskazaniu do niego.

     ![Tekst błędu dla cout](../ide/media/c-ide-couterror.png "IDE_CoutError C ++")

     Komunikat o błędzie pojawia się również w **lista błędów** okna. Okno, można wyświetlić, na pasku menu, wybierając **widoku**, **lista błędów**.

     [Cout](http://msdn.microsoft.com/library/d87db6c3-e4e1-4d09-9ec5-458f55018257) znajduje się w \<iostream\> pliku nagłówka.

2.  Aby dołączyć nagłówku iostream, wprowadź następujący kod po `#include "stdafx.h"`:

    ```
    #include \<iostream\>
    using namespace std;
    ```

     Należy zauważyć, jak kod został wprowadzony, podając sugestie dotyczące znaków, które zostały wprowadzone pojawiły się polem. To pole jest częścią technologii IntelliSense języka C++, która zawiera monity kodowania, łącznie z wyświetleniem listy elementów członkowskich klasy lub interfejsu i informacje o parametrach. Można również użyć fragmentów kodu, które są wstępnie zdefiniowane bloków kodu. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md) i [fragmenty kodu](../ide/code-snippets.md).

     Czerwona linia falista pod `cout` znika po naprawieniu błędu.

3.  Zapisz zmiany w pliku.

     ![Kod, który poprawki błędów cout](../ide/media/c-ide-coutfix.png "IDE_CoutFix C ++")

##  <a name="BKMK_DebugTest"></a> Debugowanie i testowanie aplikacji
 Można debugować GreetingsConsoleApp, aby zobaczyć, czy wyraz "Hello" jest wyświetlana w oknie konsoli.

#### <a name="to-debug-the-application"></a>Aby debugować aplikację

-   Uruchom debuger.

     ![Rozpocznij debugowanie poleceń w menu Debugowanie](../ide/media/exploreide-startdebugging.png "ExploreIDE StartDebugging")

     Debuger zaczyna się i uruchamia kod. W oknie konsoli (oddzielne okno przypominającą wiersza polecenia) pojawia się na kilka sekund, ale zamyka się szybko, gdy debuger przestanie działać. Aby wyświetlić tekst, należy ustawić punkt przerwania, aby zatrzymać wykonywanie programów.

#### <a name="to-add-a-breakpoint"></a>Aby dodać punkt przerwania

1. Dodaj punkt przerwania na pasku menu, w wierszu `return 0;`. Możesz też po prostu kliknąć na lewym marginesie, aby ustawić punkt przerwania.

    ![Przełącz punkt przerwania — polecenie w menu Debugowanie](../ide/media/exploreide-togglebreakpoint.png "togglebreakpoint — ExploreIDE")

    Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.

2. Wybierz klawisz F5, aby rozpocząć debugowanie.

    Uruchamia debuger, i okno konsoli wyświetlona wyraz **Hello**.

    ![Tekst w oknie wiersza polecenia Windows Hello](../ide/media/c-ide-hellocommandwindow.png "IDE_HelloCommandWindow C ++")

3. Naciśnij klawisze SHIFT + F5, aby zatrzymać debugowanie.

   Aby uzyskać więcej informacji, zobacz [projekty startowe](../debugger/debugging-preparation-console-projects.md).

##  <a name="BKMK_BuildRelease"></a> Tworzenie dystrybucyjnej wersji aplikacji
 Teraz, gdy masz już pewność, że wszystko działa, możesz przygotować wersję dystrybucyjną aplikacji.

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Aby wyczyścić pliki rozwiązań i zbudować wersję przeznaczoną do publikacji

1. Na pasku menu należy usunąć pliki pośrednie i pliki wyjściowe, które zostały utworzone podczas poprzednich kompilacji.

    ![Polecenie Wyczyść rozwiązanie, w menu kompilacja](../ide/media/exploreide-cleansolution.png "ExploreIDE CleanSolution")

2. Zmień konfigurację kompilacji dla GreetingsConsoleApp z **debugowania** do **wersji**.

    ![Tworzenie dystrybucyjnej wersji aplikacji](../ide/media/c-ide-changingbuildtorelease.png "IDE_ChangingBuildtoRelease C ++")

3. Skompiluj rozwiązanie.

    ![Kompiluj rozwiązanie, polecenie w menu kompilacja](../ide/media/exploreide-buildsolution.png "Skompiluj rozwiązanie ExploreIDE")

   Gratulujemy zakończenia instruktażu! Jeśli chcesz poznać więcej przykładów, zobacz [Visual Studio Samples](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [wskazówki dotyczące produktywności](../ide/productivity-tips-for-visual-studio.md) [przykłady Visual Studio](../ide/visual-studio-samples.md) [Rozpocznij tworzenie aplikacji za pomocą programu Visual Studio](../ide/get-started-developing-with-visual-studio.md)
