---
title: Wprowadzenie do testów jednostkowych
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11fb8fe4b30aa986a6c442278d1e8984604a6794
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927987"
---
# <a name="get-started-with-unit-testing"></a>Wprowadzenie do testów jednostkowych

Aby zdefiniować i uruchomić testy jednostkowe do utrzymania kondycji kodu, upewnij się, pokrycie kodu i Znajdź błędy i usterek, zanim klienci, należy użyć programu Visual Studio. Uruchamianie testów jednostkowych często, aby upewnić się, że Twój kod działa poprawnie.

## <a name="create-unit-tests"></a>Tworzenie testów jednostkowych

Tej sekcji opisano na wysokim poziomie, jak utworzyć projekt testów jednostkowych.

> [!TIP]
> Projektu, nazwę "HelloWorld" jest przykładowy projekt i żaden kod dla niej jest przeznaczony do wyświetlenia. Jeśli chcesz utworzyć projekt "nazwę HelloWorld" do testowania, zobacz [tworzenia pierwszej C# aplikacja konsolowa](../ide/quickstart-csharp-console.md). Aby uzyskać szczegółowy przewodnik, zobacz [tworzenia i uruchamiania testów dla kodu zarządzanego](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

1. Utwórz projekt testów jednostkowych.

   ![Dodaj projekt testu jednostkowego do rozwiązania](media/createunittest1.png)

1. Nazwij swój projekt.

   ![Szablon projektu testu jednostki](media/createunittest2.png)

   Projekt jest dodawany do rozwiązania.

   ![Projekt testów jednostkowych w Eksploratorze rozwiązań](media/createunittest5.png)

1. W projekcie testu jednostki Dodaj odwołanie do projektu, który ma zostać przetestowana.

   ![Dodaj odwołanie do projektu testu jednostkowego](media/createunittest6.png)

1. Wybierz projekt, który zawiera kod, przetestowania.

   ![Wybierz odwołania do dodania](media/createunittest7.png)

1. Zakoduj test jednostki.

   ![Dodaj kod do testu jednostkowego](media/createunittest8.png)

Można również utworzyć testy jednostkowe metoda wycinków z **Utwórz testy jednostkowe** [polecenia](create-unit-tests-menu.md).

![Za pomocą polecenia Utwórz testy jednostki](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

1. Otwórz **Eksplorator testów**.

   ![W menu Test Otwórz Eksploratora testów](media/rununittest1.png)

1. Uruchamianie testów jednostkowych.

   ![Uruchamianie testów jednostkowych w Eksploratorze testów](media/rununittest2.png)

   Możesz zobaczyć testy jednostek zakończone powodzeniem i niepowodzeniem w **Eksplorator testów**.

   ![Przejrzyj wyniki testów jednostek w Eksploratorze testów](media/rununittest3.png)

## <a name="view-live-unit-test-results"></a>Wyświetlanie wyników testów jednostek na żywo

Jeśli używasz MSTest, xUnit i NUnit struktura testowania w programie Visual Studio 2017 lub nowszego, zostanie wyświetlony na żywo wyniki testów jednostkowych.

> [!NOTE]
> Testowanie jednostek na żywo jest tylko dostępne w Visual Studio 2017 Enterprise Edition.

1. Włącz testowanie z jednostek na żywo **testu** menu.

   ![Włącz testy jednostkowe na żywo](media/live-test-results-start.png)

1. Wyświetl wyniki testów w ramach okna edytora kodu, wpisywania i edytowania kodu.

   ![Wyświetlanie wyników testów](media/live-test-results-ui.png)

1. Wybierz test wskaźniki wyników, aby uzyskać więcej informacji.

   ![Wybierz wskaźniki wyników testu](media/live-test-results-details.png)

Aby uzyskać więcej informacji, zobacz [testy jednostkowe na żywo](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generowanie testów jednostkowych za pomocą funkcji IntelliTest

Po uruchomieniu testów funkcji IntelliTest, można łatwo zobaczyć, testy, które kończą się niepowodzeniem i Dodaj wszelkie niezbędne kod, aby je rozwiązać. Możesz wybrać, które wygenerowanych testów, aby zapisać do projektu testowego, aby zapewnić mechanizm regresji. W przypadku zmiany kodu, należy ponownie uruchomić program IntelliTest w celu synchronizowania wygenerowanych testów wprowadzania zmian w kodzie. Aby dowiedzieć się więcej, zobacz temat [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

![Generowanie testów jednostkowych za pomocą funkcji IntelliTest](media/intellitest.png)

## <a name="run-unit-tests-with-test-explorer"></a>Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów

Użyj **Eksploratora testów** do uruchamiania testów jednostkowych z Visual Studio lub projektów testów jednostkowych innych firm, grupowanie testów w kategorie, filtrowanie listy testów, tworzenie, zapisywanie i uruchamianie list odtwarzania testów. Możesz również debugować testy i analizowanie testów wydajność i pokrycie kodu. Aby dowiedzieć się więcej, zobacz temat [Uruchamianie testów jednostkowych w Eksploratorze testów](../test/run-unit-tests-with-test-explorer.md).

![Uruchamianie testów jednostkowych w Eksploratorze testów](media/testexplorer.png)

## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie zabezpieczyć się przed błędami, testy powinny uwzględniać znaczną część kodu. Aby dowiedzieć się więcej, zobacz temat [użycie pokrycia kodu, aby ustalić, ile kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-different-unit-test-framework"></a>Używać różnych testów jednostkowych

Można uruchomić testy jednostkowe w programie Visual Studio, za pomocą platform testowych innych firm, takich jak zwiększenie wydajności, Google i NUnit. Użyj wtyczki dla struktury modułu uruchamiającego testy w tym Visual Studio może więc pracować z tą strukturą.

Poniżej przedstawiono kroki, aby włączyć platform testowych innych firm:

1. Wybierz **narzędzia** > **rozszerzenia i aktualizacje** z paska menu.

1. W **rozszerzenia i aktualizacje** okna dialogowego rozwiń **Online** kategorii i następnie **Visual Studio Marketplace**. Następnie wybierz **narzędzia** > **testowania**.

   ![Visual Studio Marketplace](media/extensions-and-updates-testing.png)

1. Wybierz framework lub chcesz zainstalować, a następnie wybierz kartę **Pobierz**.

1. Utwórz projekt biblioteki klas i dodaj go do rozwiązania.

   ![Nazwij projekt biblioteki klas i dodaj go](media/create3rdpartyunittest3.png)

1. Zainstaluj wtyczkę. W **Eksploratora rozwiązań**, wybierz projekt biblioteki klas, a następnie wybierz **Zarządzaj pakietami NuGet** menu kliknij prawym przyciskiem myszy lub kontekstu.

   ![Zarządzaj pakietami NuGet, aby zainstalować dodatek typu plug-in](media/create3rdpartyunittest3a.png)

   [NuGet](https://www.nuget.org/) to rozszerzenie programu Visual Studio, który służy do dodawania i aktualizowania bibliotek i narzędzi dla projektów.

1. W **Menedżera pakietów NuGet** okna, wyszukaj i wybierz dodatek, a następnie wybierz **zainstalować**.

   ![Zainstaluj preferowanej struktury firm 3](media/create3rdpartyunittest4.png)

   Struktura ma odwołania w projekcie.

   ![Odwołanie do testów jednostkowych innych firm 3 zostanie dodany do rozwiązania](media/create3rdpartyunittest6.png)

1. W projekcie biblioteki klas **odwołania** węzeł **Dodaj odwołanie**.

   ![Dodaj odwołanie do projektu](media/createunittest6.png)

1. W **Menadżer odwołań** okna dialogowego Wybierz projekt, który zawiera kod, przetestowania.

   ![Wybierz projekt kodu do przetestowania](media/createunittest7.png)

1. Zakoduj test jednostki.

   ![Dodaj kod do pliku kodu testu jednostki](media/create3rdpartyunittest7.png)

## <a name="see-also"></a>Zobacz także

* [Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Polecenie Utwórz testy jednostkowe](create-unit-tests-menu.md)
* [Generuj testy z funkcją IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Uruchom testy z Eksploratora testów](run-unit-tests-with-test-explorer.md)
* [Określić pokrycia kodu](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Poprawianie jakości kodu](improve-code-quality.md)