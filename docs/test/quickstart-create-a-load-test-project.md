---
title: Tworzenie projektu testu wydajności i obciążenia sieci Web
description: Dowiedz się, jak utworzyć i uruchomić projekt testów wydajności i obciążenia sieci Web w programie Visual Studio za pomocą tego przewodnika Szybki Start.
ms.custom: SEO-VS-2020
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3833542dc00f347014dabf96f836fbd4fa810862
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329136"
---
# <a name="quickstart-create-a-load-test-project"></a>Szybki start: Tworzenie projektu testu obciążeniowego

W tym 10-minutowym samouczku szybki start dowiesz się, jak utworzyć i uruchomić projekt testów wydajności i obciążenia sieci Web w programie Visual Studio. Testy obciążenia wykonują wydajność sieci Web lub testy jednostkowe, aby symulować wielu użytkowników uzyskujących dostęp do serwera w tym samym czasie.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Wymagania dotyczące oprogramowania

Projekty testów wydajności i obciążenia sieci Web są dostępne tylko w **wersji Enterprise** programu Visual Studio.

## <a name="install-the-load-testing-component"></a>Zainstaluj składnik testowania obciążenia

Jeśli składnik narzędzi testowania wydajności sieci Web i obciążenia nie został jeszcze zainstalowany, należy zainstalować go za pomocą Instalator programu Visual Studio.

1. Otwórz **Instalator programu Visual Studio** z menu **Start** systemu Windows. Możesz również uzyskać do niego dostęp w programie Visual Studio z okna dialogowego Nowy projekt lub wybierając **Narzędzia**  >  **Pobierz narzędzia i funkcje** z paska menu.

1. W **Instalator programu Visual Studio** wybierz kartę **poszczególne składniki** i przewiń w dół do sekcji **debugowanie i testowanie** . Wybierz pozycję **Narzędzia do testowania obciążenia i wydajności sieci Web**.

   ![Składnik narzędzi do testowania wydajności sieci Web i testów obciążenia](media/web-perf-load-testing-tools-component.png)

1. Wybierz przycisk **Modyfikuj** .

   Składnik narzędzi do testowania wydajności sieci Web i testu obciążenia jest zainstalowany.

## <a name="create-a-load-test-project"></a>Tworzenie projektu testu obciążeniowego

W tej sekcji utworzymy projekt testu obciążenia języka C#. Możesz również utworzyć projekt testu obciążenia Visual Basic, jeśli wolisz.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. Wybierz pozycję **plik** > **Nowy** > **projekt** z paska menu.

   Zostanie otwarte okno dialogowe **Nowy projekt** .

3. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowane** i **Visual C#**, a następnie wybierz kategorię **test** . Wybierz szablon **projektu test wydajności i obciążenia sieci Web** .

   ![Szablon projektu testu wydajności i obciążenia sieci Web](media/web-perf-load-test-project-template.png)

4. Wprowadź nazwę projektu, jeśli nie chcesz używać nazwy domyślnej, a następnie wybierz **przycisk OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wpisz **test sieci Web** w polu wyszukiwania, a następnie wybierz szablon **projekt testu wydajności i obciążenia sieci Web jako \[ przestarzały]** dla języka C#. Wybierz pozycję **Next** (Dalej).

4. Wprowadź nazwę projektu, jeśli nie chcesz używać nazwy domyślnej, a następnie wybierz pozycję **Utwórz**.

::: moniker-end

   Program Visual Studio tworzy projekt i wyświetla pliki w **Eksplorator rozwiązań**. Projekt początkowo zawiera jeden plik testu sieci Web o nazwie *WebTest1. webtest*.

## <a name="add-a-load-test-to-the-project"></a>Dodaj test obciążenia do projektu

1. W menu rozwijanym prawym przyciskiem myszy lub menu kontekstowym węzła projektu w **Eksplorator rozwiązań** wybierz pozycję **Dodaj**  >  **test obciążenia**.

   Zostanie otwarty **nowy Kreator testu obciążeniowego** .

1. Wybierz opcję **lokalny test obciążenia** , a następnie wybierz przycisk **dalej**. Więcej informacji na temat testowania obciążenia opartego na chmurze można znaleźć [tutaj](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true).

   ![Kreator nowego testu obciążenia — Pierwsza Strona](media/load-test-wizard-page-1.png)

1. Wybierz pozycję **dalej** , aby przejść przez kreatora do momentu, aż osiągniesz **scenariusz Dodawanie testów do scenariusza testu obciążenia i edytujesz stronę testu mieszanego** . Wybierz przycisk **Dodaj**.

   Zostanie otwarte okno dialogowe **Dodawanie testów** .

1. W obszarze **dostępne testy** wybierz pozycję **WebTest1**, a następnie wybierz strzałkę w prawo, aby przenieść ją do pola **Wybrane testy** . Wybierz przycisk **OK** .

   ![Okno dialogowe Dodawanie testów](media/add-tests-dialog-box.png)

1. W **nowej Kreator testu obciążeniowego** kliknij przycisk **Zakończ** .

   Test obciążenia zostanie dodany do projektu, a plik testu obciążenia zostanie otwarty w oknie edytora.

## <a name="run-the-load-test"></a>Uruchom test obciążenia

Utworzyliśmy test obciążenia, który nie jest bardzo dużo, ale Uruchommy go mimo to.

Z menu po kliknięciu prawym przyciskiem myszy lub menu kontekstowego testu obciążenia, który jest otwarty w edytorze, wybierz polecenie **Uruchom test obciążenia**.

![Uruchom menu testu obciążenia](media/run-load-test.png)

Test obciążenia rozpocznie działanie. Okno **wyniki testów** pokazuje, że test jest w toku, a Analizator testu obciążenia jest wyświetlany w oknie edytora. Po zakończeniu testu, który powinien być pięć minut, jeśli wartości domyślne zostały zaakceptowane, w edytorze zostanie wyświetlony podsumowanie. Możesz wybrać **wykresy**, **tabele** lub **szczegóły** , aby uzyskać różne informacje dotyczące wyników testu obciążenia.

![Okno analizatora testu obciążenia](media/load-test-analyzer.png)

## <a name="next-steps"></a>Następne kroki

Po utworzeniu projektu prostego testu obciążenia następnym krokiem jest skonfigurowanie scenariuszy, zestawów liczników i parametrów uruchomieniowych.

> [!div class="nextstepaction"]
> [Edytuj ustawienia testu](edit-load-tests.md)
