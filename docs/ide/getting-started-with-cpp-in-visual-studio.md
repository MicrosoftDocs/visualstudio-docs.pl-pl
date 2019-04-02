---
title: Wprowadzenie do języka C++
description: ''
ms.custom: mvc
ms.date: 12/04/2017
ms.topic: tutorial
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: 375879e6a6aba93b702c65412328458a9a5568ab
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790345"
---
# <a name="get-started-with-c-in-visual-studio"></a>Wprowadzenie do języka C++ w programie Visual Studio

Wykonaj ten przewodnik Szybki Start, aby zapoznać się z wielu narzędzi i oknach dialogowych, używane podczas tworzenia aplikacji w języku C++ w programie Visual Studio. Tworzenie "Hello, World"-stylów aplikacji konsoli, a dowiesz się więcej na temat pracy w zintegrowanym środowisku programistycznym (IDE).

## <a name="prerequisites"></a>Wymagania wstępne

Nie trzeba znać przy użyciu języka C++, aby ukończyć ten przewodnik Szybki Start, ale należy zapoznać się z ogólnych programowanie i debugowanie pojęcia. Dokumentacja programu Visual Studio nie pokazują, jak programować w języku C++. Przewodnik dobre zasoby do nauki języka c++ jest [wprowadzenie](https://isocpp.org/get-started) strony w witrynie sieci Web ISO C++.

::: moniker range="vs-2017"

W tym samouczku potrzebujesz kopii programu Visual Studio 2017 z **programowanie aplikacji klasycznych w języku C++** zainstalowanym obciążeniem. Szybki przewodnik dotyczący instalacji, zobacz [Instalowanie obsługi języka C++ w programie Visual Studio](/cpp/build/vscpp-step-0-installation).

::: moniker-end

::: moniker range=">=vs-2019"

W tym samouczku potrzebujesz kopii programu Visual Studio 2019 r przy użyciu **programowanie aplikacji klasycznych w języku C++** zainstalowanym obciążeniem. Szybki przewodnik dotyczący instalacji, zobacz [Instalowanie obsługi języka C++ w programie Visual Studio](/cpp/build/vscpp-step-0-installation).

::: moniker-end

## <a name="create-a-console-app"></a>tworzenie aplikacji konsoli

Jeśli nie jest jeszcze uruchomiona, Otwórz program Visual Studio.

::: moniker range="vs-2017"

![Środowisko IDE z Visual C&#43; &#43; zastosowanych ustawień](../ide/media/get-started-cpp-ide-layout.png)

Po otwarciu programu Visual Studio, można wyświetlić trzy podstawowe części IDE: narzędzie systemu windows, menu i paski narzędzi oraz przestrzeń głównego okna. Okna narzędziowe są zadokowane po lewej i prawej stronie okna aplikacji. **Szybkie uruchamianie** pola, paska menu i standardowy pasek narzędzi znajdują się u góry. Zawiera środek okna **strona startowa**. Po otwarciu rozwiązania lub projektu, w tym miejscu pojawiają się edytory i projektanty. Podczas opracowywania aplikacji, większość czasu odbywa się w tym środkowym obszarze.

::: moniker-end

::: moniker range=">=vs-2019"

Po otwarciu programu Visual Studio, w oknie uruchamiania pojawia się jako pierwsza. Wybierz **Kontynuuj bez konieczności pisania kodu** otworzyć środowisko programistyczne.

Zobaczysz trzy podstawowe części IDE: narzędzie systemu windows, menu i paski narzędzi oraz przestrzeń głównego okna. Okna narzędziowe są zadokowane po lewej i prawej stronie okna aplikacji. Pole wyszukiwania, pasek menu i standardowy pasek narzędzi znajdują się u góry. Podczas ładowania rozwiązania lub projektu, edytory i projektanty są wyświetlane w centralne miejsce w oknie aplikacji. Podczas opracowywania aplikacji spędzisz większość czasu w tym środkowym obszarze.

::: moniker-end

Program Visual Studio używa *projektów* organizowania kodu dla aplikacji, a *rozwiązania* do organizowania projektów. Projekt zawiera wszystkie opcje, konfiguracji i reguły używane do tworzenia aplikacji. Umożliwia także zarządzanie relacji między plików wszystkich projektów i plików zewnętrznych. Aby utworzyć aplikację, najpierw należy utworzyć nowy projekt i rozwiązanie.

### <a name="to-create-a-console-app-project"></a>Aby utworzyć projekt aplikacji konsoli

1. Na pasku menu wybierz **Plik > Nowy > Projekt** otworzyć **nowy projekt** okno dialogowe.

   ![Na pasku menu wybierz pozycję Plik > Nowy > Projekt](../ide/media/get-started-cpp-file-new-project-menu.png)

1. W **nowy projekt** okno dialogowe, wybierz opcję **zainstalowane > Visual C++** Jeśli nie została jeszcze wybrana. W środkowym okienku wybierz **aplikacji konsoli Windows** szablonu. W **nazwa** edytować pole, wprowadź *HelloApp*.

   ![Użyj okna dialogowego Nowy projekt do utworzenia projektu aplikacji](../ide/media/get-started-cpp-new-project-dialog.png)

   Twoje okno dialogowe może mieć różne opcje w zależności od obciążeń programu Visual Studio i składniki, które zostały zainstalowane. Jeśli nie widzisz szablony projektów Visual C++, musisz ponownie uruchomić Instalatora programu Visual Studio i zainstaluj **programowanie aplikacji klasycznych w języku C++** obciążenia. Można to zrobić bezpośrednio z **nowy projekt** okna dialogowego. Aby uruchomić Instalatora, wybierz opcję **Otwórz Instalator programu Visual Studio** link w oknie dialogowym.

1. Wybierz **OK** przycisk, aby utworzyć rozwiązanie i projekt aplikacji.

   HelloApp projektu i rozwiązania przy użyciu podstawowych plików dla aplikacji konsoli Windows, są tworzone i ładowane automatycznie do **Eksploratora rozwiązań**. *HelloApp.cpp* plik jest otwarty w edytorze kodu. Te elementy są wyświetlane w **Eksploratora rozwiązań**:

   ![Pliki rozwiązania w Eksploratorze rozwiązań](../ide/media/get-started-cpp-solution-explorer.png)

## <a name="add-code-to-the-app"></a>Dodaj kod do aplikacji

Następnie dodaj kod, aby wyświetlić wyraz "Hello" w oknie konsoli.

### <a name="to-edit-code-in-the-editor"></a>Edytowanie kodu w edytorze

1. W *HelloApp.cpp* plików, należy wprowadzić pusty wiersz przed wierszem `return 0;` a następnie wprowadź ten kod:

   ```cpp
   cout << "Hello\n";
   ```

   Czerwona linia falista jest wyświetlany w obszarze `cout`. Jeśli wskaźnik znajduje się nad nim, pojawi się komunikat o błędzie.

   ![Tekst błędu dla cout](../ide/media/get-started-cpp-intellisense-error.png)

   Komunikat o błędzie pojawia się również w **lista błędów** okna. W tym oknie można wyświetlić, wybierając **Widok > Lista błędów** na pasku menu.

   ![Błąd w oknie Lista błędów](../ide/media/get-started-cpp-error-list.png)

   Brak deklaracji dla kodu [std::cout](/cpp/standard-library/iostream), który znajduje się w  *\<iostream >* pliku nagłówka.

1. Aby uwzględnić *iostream* nagłówka, wprowadź ten kod po `#include "stdafx.h"`:

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   Należy zauważyć, jak kod został wprowadzony pojawiły się polem. To pole zawiera sugestie automatycznego uzupełniania dla wprowadzanych znaków. Tego część funkcji C++ IntelliSense, co zapewnia monity kodowania, w tym elementów członkowskich klasy lub interfejsu i informacje o parametrach. Można również użyć fragmentów kodu, które są wstępnie zdefiniowane bloków kodu. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md) i [fragmenty kodu](../ide/code-snippets.md).

   ![Naprawiono kodu w edytorze](../ide/media/get-started-cpp-cout-fix.png)

   Czerwona linia falista pod `cout` znika po naprawieniu błędu.

1. Aby zapisać zmiany w pliku, naciśnij klawisz **Ctrl + S**.

## <a name="build-the-app"></a>Tworzenie aplikacji

Jest łatwy do kompilacji kodu. Na pasku menu wybierz **kompilacji > Kompiluj rozwiązanie**. Program Visual Studio tworzy rozwiązanie HelloApp i raportów postępu w **dane wyjściowe** okna.

   ![Skompiluj rozwiązanie HelloApp](../ide/media/get-started-cpp-build-solution.gif)

## <a name="debug-and-test-the-app"></a>Debugowanie i testowanie aplikacji

Można debugować HelloApp, aby zobaczyć, czy wyraz "Hello" jest wyświetlana w oknie konsoli.

### <a name="to-debug-the-app"></a>Aby debugować aplikację

Aby uruchomić debugera, wybierz **Debuguj > Rozpocznij debugowanie** na pasku menu.

![Start Debugging, polecenie w menu Debugowanie](../ide/media/get-started-cpp-start-debugging-menu.png)

Debuger zaczyna się i uruchamia kod. W oknie konsoli (oddzielne okno przypominającą wiersza polecenia) pojawia się na kilka sekund, ale zamyka się szybko, gdy debuger przestanie działać. Aby wyświetlić tekst, należy ustawić punkt przerwania, aby zatrzymać wykonywanie programów.

### <a name="to-add-a-breakpoint"></a>Aby dodać punkt przerwania

1. W edytorze, umieść kursor w wierszu `return 0;`. Na pasku menu wybierz **Debuguj > Przełącz punkt przerwania**. Możesz również kliknąć na lewym marginesie, aby ustawić punkt przerwania.

     ![Przełącz punkt przerwania — polecenie w menu Debugowanie](../ide/media/get-started-cpp-toggle-breakpoint-menu.png)

     Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.

     ![Punkt przerwania, wskazane w oknie margines](../ide/media/get-started-cpp-breakpoint-set.png)

1. Aby rozpocząć debugowanie, naciśnij klawisz **F5**.

   Uruchamia debuger, i okno konsoli wyświetlona wyraz **Hello**.

   ![Tekst Witaj w oknie konsoli](../ide/media/get-started-cpp-helloapp-window.png)

1. Aby zatrzymać debugowanie, naciśnij klawisz **Shift + F5**.

Aby uzyskać więcej informacji na temat debugowania projektu konsoli Zobacz [projekty konsoli](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a>Tworzenie dystrybucyjnej wersji aplikacji

Teraz, gdy upewnieniu się, że wszystko działa, możesz przygotować wersję dystrybucyjną aplikacji. Wersja kompilacji pozostaw informacji o debugowaniu i opcje optymalizacji kompilatora Użyj tworzyć mniejszy, szybszy kod.

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Aby wyczyścić pliki rozwiązań i zbudować wersję przeznaczoną do publikacji

1. Na pasku menu wybierz **kompilacji > czyste rozwiązanie** można usunąć pliki pośrednie i pliki wyjściowe, które zostały utworzone podczas poprzednich kompilacji.

   ![Polecenie Wyczyść rozwiązanie, w menu kompilacji](../ide/media/get-started-cpp-clean-solution-menu.png)

1. Aby zmienić konfigurację rozwiązania HelloApp z **debugowania** do **wersji**, na pasku narzędzi wybierz na liście rozwijanej na formant konfiguracje rozwiązania, a następnie wybierz **wersji**.

   ![Tworzenie dystrybucyjnej wersji tej aplikacji](../ide/media/get-started-cpp-set-release-configuration.png)

1. Skompiluj rozwiązanie. Na pasku menu wybierz **kompilacji > Kompiluj rozwiązanie**.

Po zakończeniu tej kompilacji, zostanie utworzona aplikacja, która możesz skopiować i uruchomić w dowolnym oknie wiersza polecenia. Nie może wykonać wiele, ale jest bramą rzeczy większą.

Gratulujemy ukończenie tego przewodnika Szybki Start!

## <a name="see-also"></a>Zobacz także

- [Za pomocą programu Visual Studio IDE do tworzenia klasycznych aplikacji języka C++](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)
- [Przewodnik: Tworzenie prostej aplikacji przy użyciu C# lub Visual Basic](../get-started/csharp/tutorial-wpf.md)
- [Porady dotyczące wydajności dla programu Visual Studio](../ide/productivity-tips-for-visual-studio.md)
