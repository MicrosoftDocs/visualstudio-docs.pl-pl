---
title: Narzędzia do testowania Visual Studio dla komputerów Mac
ms.date: 08/03/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: 758bdcb0d854247847e4d0d56152840643402bf4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91580964"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Narzędzia do testowania w Visual Studio dla komputerów Mac

Narzędzia do testowania Visual Studio dla komputerów Mac mogą pomóc Ci w rozwojem i utrzymywaniu wysokich standardów doskonałości kodu. Testy jednostkowe można pisać i uruchamiać przy użyciu struktury testów jednostkowych firmy Microsoft (MSTest), xUnit lub NUnit.

## <a name="creating-tests"></a>Tworzenie testów
Aby rozpocząć testowanie, możesz utworzyć nowy projekt testowy w rozwiązaniu, klikając rozwiązanie prawym przyciskiem myszy i wybierając polecenie **dodaj > nowy projekt...** . Następnie wybierz jedną z kategorii testów po lewej stronie okna dialogowego (na przykład kategorię **testy > sieci Web i konsoli** ). Wybierz typ projektu testowego, który chcesz utworzyć, a następnie kliknij przycisk Dalej. Postępuj zgodnie z instrukcjami wyświetlanymi w oknach dialogowych, a następnie do rozwiązania zostanie dodany nowy projekt testowy.

![Okno dialogowe Nowy projekt z zaznaczoną sekcją testów > sieci Web i konsoli, pokazująca projekty xUnit, MSTest i NUnit](media/create-new-test-project.PNG)

> [!NOTE]
> Aby uzyskać więcej informacji na temat testowania jednostkowego aplikacji platformy .NET Core i wybierania platform testów jednostkowych, zobacz [testy jednostkowe w programie .NET Core i w .NET Standard](/dotnet/core/testing/?pivots=xunit) dokumentacji.

## <a name="running-tests"></a>Uruchamianie testów
Okno **testy jednostkowe** służy do uruchamiania testów jednostkowych i jest otwierane za pomocą menu **Widok > konsole > testy jednostkowe** . Testy jednostkowe w rozwiązaniu są automatycznie wykrywane i wyświetlane w tym oknie, w którym można uruchomić wszystkie testy lub zestaw testów, które zostały wybrane.

![Okno testowe pokazujące listę testów jednostkowych i pasek narzędzi służący do uruchamiania lub zatrzymywania testów.](media/test-window.PNG)

Podczas edytowania klasy języka C#, która zawiera testy jednostkowe, można uruchomić testy, klikając prawym przyciskiem myszy klasę testową lub metodę testową i wybierając menu **Run test (s)** lub **test debugowania** . Wybranie elementu menu **Uruchom** testy spowoduje uruchomienie testów w oknie testowym, wybranie menu **test debugowania** spowoduje takie samo i dołączenie debugera, aby umożliwić Rozwiązywanie problemów z kodem.

![Menu po kliknięciu prawym przyciskiem myszy z opcjami uruchamiania i debugowania testów](media/run-tests-context-menu.PNG)

Gdy testy są uruchomione, zostanie wyświetlone okno **wyniki testów** , aby można było przejrzeć testy zakończone powodzeniem lub zakończone niepowodzeniem oraz dane wyjściowe uruchamiania tych testów.

![Okno wyników testu przedstawiające jeden test zakończony niepowodzeniem oraz liczbę 21 testów zakończonych powodzeniem i 1 Test zakończony niepowodzeniem.](media/test-results-window.PNG)

## <a name="see-also"></a>Zobacz też

- [Testy jednostkowe w .NET Core i .NET Standard](/dotnet/core/testing)
- [Wprowadzenie do testów jednostkowych (Visual Studio w systemie Windows)](/visualstudio/test/getting-started-with-unit-testing)
- [Podstawowe informacje o teście jednostkowym (Visual Studio w systemie Windows)](/visualstudio/test/unit-test-basics)