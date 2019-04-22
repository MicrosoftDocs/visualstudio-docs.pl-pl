---
title: Wprowadzenie do testów jednostkowych
ms.date: 04/01/2019
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3f3537a56b746c9104898d68e40038fcd545910
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58856463"
---
# <a name="get-started-with-unit-testing"></a>Wprowadzenie do testów jednostkowych

Aby zdefiniować i uruchomić testy jednostkowe do utrzymania kondycji kodu, upewnij się, pokrycie kodu i Znajdź błędy i usterek, zanim klienci, należy użyć programu Visual Studio. Uruchamianie testów jednostkowych często, aby upewnić się, że Twój kod działa poprawnie.

## <a name="create-unit-tests"></a>Tworzenie testów jednostkowych

Tej sekcji opisano na wysokim poziomie, jak utworzyć projekt testów jednostkowych.

> [!TIP]
> Projekt testowany "HelloWorldCore" jest przykładowy projekt i żaden kod dla niej jest przeznaczony do wyświetlenia. Jeśli chcesz utworzyć projekt "Hello World" do testowania, zobacz [tworzenia pierwszej C# aplikacja konsolowa](../ide/quickstart-csharp-console.md). Aby uzyskać szczegółowy przewodnik, zobacz [tworzenia i uruchamiania testów dla kodu zarządzanego](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

1. Otwórz projekt, który chcesz przetestować w programie Visual Studio.

1. W **Eksploratora rozwiązań**, wybierz węzeł rozwiązania. Następnie na pasku menu u góry wybierz **pliku** > **Dodaj** > **nowy projekt**.

1. Okno dialogowe Nowy projekt zawiera to test jednostkowy szablon projektu służący do struktury testów, które chcesz użyć i wybierz ją.

   ::: moniker range=">=vs-2019"

   ![Szablon projektu testu jednostki w programie Visual Studio 2019 r.](media/vs-2019/add-new-test-project.png)

   Kliknij przycisk **dalej**, wybierz nazwę dla projektu testowego, a następnie kliknij przycisk **Utwórz**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Szablon projektu testu jednostki w programie Visual Studio 2019 r.](media/mstest-test-project-template.png)

   Wybierz nazwę dla projektu testowego, a następnie kliknij przycisk **OK**.

   ::: moniker-end

   Projekt jest dodawany do rozwiązania.

   ![Projekt testów jednostkowych w Eksploratorze rozwiązań](media/vs-2019/solution-explorer.png)

1. W projekcie testu jednostki Dodaj odwołanie do projektu, którą chcesz przetestować, klikając prawym przyciskiem myszy **odwołania** lub **zależności** , a następnie wybierając **Dodaj odwołanie**.

1. Wybierz projekt, który zawiera kod, można przetestować i kliknij przycisk **OK**.

   ![Dodaj odwołanie do projektu w programie Visual Studio](media/vs-2019/reference-manager.png)

1. Dodaj kod do metody testowej jednostki.

   ![Dodaj kod do metody testów jednostkowych w programie Visual Studio](media/vs-2019/unit-test-method.png)

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

1. Otwórz [Eksplorator testów](../test/run-unit-tests-with-test-explorer.md) , wybierając **testu** > **Windows** > **Eksplorator testów** na pasku menu u góry.

1. Uruchom testy jednostkowe, klikając pozycję **Uruchom wszystkie**.

   ![Uruchamianie testów jednostkowych w Eksploratorze testów](media/vs-2019/test-explorer-run-all.png)

   Po zakończeniu testów, zielony znacznik wyboru wskazuje, że test zakończony pomyślnie. Ikona z czerwonym symbolem "x" oznacza, że test nie powiódł się.

   ![Przejrzyj wyniki testów jednostek w Eksploratorze testów](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Możesz użyć [Eksploratora testów](../test/run-unit-tests-with-test-explorer.md) do uruchamiania testów jednostkowych ze struktury testów wbudowanych (MSTest) lub z innych środowisk testów. Można grupowanie testów w kategorie, filtrowanie listy testów i tworzenie, zapisywanie i uruchamianie list odtwarzania testów. Możesz również debugować testy i analizowanie testów wydajność i pokrycie kodu.

## <a name="view-live-unit-test-results"></a>Wyświetlanie wyników testów jednostek na żywo

Jeśli używasz MSTest, xUnit i NUnit struktura testowania w programie Visual Studio 2017 lub nowszego, zostanie wyświetlony na żywo wyniki testów jednostkowych.

> [!NOTE]
> Testowanie jednostek na żywo jest dostępna w Enterprise edition.

1. Włącz testowanie z jednostek na żywo **testu** menu, wybierając **testu** > **Live Unit Testing** > **Start**.

   ::: moniker range="vs-2017"

   ![Włącz testy jednostkowe na żywo](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Rozpocznij live unit testing w programie Visual Studio 2019 r.](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Wyświetl wyniki testów w ramach okna edytora kodu, wpisywania i edytowania kodu.

   ![Wyświetlanie wyników testów](media/vs-2019/live-unit-testing-results.png)

1. Kliknij wskaźnik wyników testu, aby uzyskać więcej informacji, takich jak nazwy testów, które obejmują tę metodę.

   ![Wybierz wskaźniki wyników testu](media/vs-2019/live-unit-testing-details.png)

Aby uzyskać więcej informacji na temat testów jednostkowych na żywo, zobacz [testy jednostkowe na żywo](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generowanie testów jednostkowych za pomocą funkcji IntelliTest

Po uruchomieniu testów funkcji IntelliTest, widać, testy, które kończą się niepowodzeniem i Dodaj wszelkie niezbędne kod, aby je rozwiązać. Możesz wybrać, które wygenerowanych testów, aby zapisać do projektu testowego, aby zapewnić mechanizm regresji. W przypadku zmiany kodu, należy ponownie uruchomić program IntelliTest w celu synchronizowania wygenerowanych testów wprowadzania zmian w kodzie. Aby dowiedzieć się więcej, zobacz temat [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

> [!TIP]
> Funkcja IntelliTest jest dostępna tylko dla kodu zarządzanego, który jest przeznaczony dla .NET Framework.

![Generowanie testów jednostkowych za pomocą funkcji IntelliTest](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Analiza pokrycia kodu

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie zabezpieczyć się przed błędami, testy powinny uwzględniać znaczną część kodu. Aby dowiedzieć się więcej, zobacz temat [użycie pokrycia kodu, aby ustalić, ile kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-third-party-test-framework"></a>Korzystaj z platformy testowych innych firm

Można uruchomić testy jednostkowe w programie Visual Studio, za pomocą platform testowych innych firm, takich jak zwiększenie wydajności, Google i NUnit. Użyj **Menedżera pakietów NuGet** można zainstalować pakietu NuGet dla wybranej platformy. Lub, xUnit i NUnit struktury testów, Visual Studio obejmują szablony projektów testowych wstępnie skonfigurowane, które zawierają niezbędne pakiety NuGet.

Aby utworzyć testy jednostkowe, które używają [NUnit](https://nunit.org/):

1. Otwórz rozwiązanie, które zawiera kod, który ma zostać przetestowana.

2. Kliknij prawym przyciskiem myszy nad rozwiązaniem w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy projekt**.

3. Wybierz **projekt testu NUnit** szablonu projektu.

   ::: moniker range=">=vs-2019"

   ![Szablon projektu testu NUnit w Visual Studio 2019 r.](media/vs-2019/nunit-test-project-template.png)

   Kliknij przycisk **dalej**, nadaj projektowi nazwę, a następnie kliknij przycisk **Utwórz**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Nadaj projektowi nazwę, a następnie kliknij przycisk **OK** do jego utworzenia.

   ::: moniker-end

   Szablon projektu zawiera odwołania do NuGet NUnit i NUnit3TestAdapter.

   ![Zależności NUnit NuGet w Eksploratorze rozwiązań](media/vs-2019/nunit-nuget-dependencies.png)

4. Dodaj odwołanie z projektu testów do projektu, który zawiera kod, który ma zostać przetestowana.

5. Dodaj kod do metody testowej.

   ![Dodaj kod do pliku kodu testu jednostki](media/vs-2019/unit-test-method.png)

6. Uruchom test z **Eksploratora testów** lub przez kliknięcie prawym przyciskiem myszy na kod testu, a następnie wybierając **Uruchom test(ów)**.

## <a name="see-also"></a>Zobacz także

* [Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Polecenie Utwórz testy jednostkowe](create-unit-tests-menu.md)
* [Generuj testy z funkcją IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Uruchom testy z Eksploratora testów](run-unit-tests-with-test-explorer.md)
* [Analiza pokrycia kodu](using-code-coverage-to-determine-how-much-code-is-being-tested.md)