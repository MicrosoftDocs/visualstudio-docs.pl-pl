---
title: Tworzenie projektu testu wydajności sieci Web i ładowania
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f186e8c10d894b98e789480046d43fc957edd8a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75566413"
---
# <a name="quickstart-create-a-load-test-project"></a>Szybki start: tworzenie projektu testu obciążeniowego

W tym 10-minutowym przewodniku Szybki start dowiesz się, jak utworzyć i uruchomić projekt testu wydajności sieci web i obciążenia w programie Visual Studio. Testy obciążenia wykonują testy wydajności sieci web lub jednostkowe, aby symulować wielu użytkowników uzyskujących dostęp do serwera w tym samym czasie.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Wymagania dotyczące oprogramowania

Projekty testów wydajności sieci Web i obciążenia są dostępne tylko w **wersji Enterprise** programu Visual Studio.

## <a name="install-the-load-testing-component"></a>Zainstaluj składnik testowania obciążenia

Jeśli nie masz jeszcze zainstalowanego składnika narzędzi do testowania wydajności sieci web i testowania obciążenia, musisz go zainstalować za pośrednictwem instalatora programu Visual Studio.

1. Otwórz **Instalatora programu Visual Studio** z menu **Start** systemu Windows. Dostęp do niego można również uzyskać w programie Visual Studio z okna dialogowego nowego projektu lub wybierając **polecenie Narzędzia** > **Pobierz narzędzia i funkcje** na pasku menu.

1. W **Instalatorze programu Visual Studio**wybierz kartę Poszczególne **składniki** i przewiń w dół do sekcji **Debugowanie i testowanie.** Wybierz **narzędzia do testowania wydajności sieci Web i testowania obciążenia**.

   ![Składnik narzędzi do testowania wydajności sieci Web i testowania obciążenia](media/web-perf-load-testing-tools-component.png)

1. Wybierz przycisk **Modyfikuj.**

   Zainstalowany jest składnik narzędzi do testowania wydajności sieci web i testowania obciążenia.

## <a name="create-a-load-test-project"></a>Tworzenie projektu testu obciążeniowego

W tej sekcji utworzymy projekt testu obciążenia języka C#. Można również utworzyć projekt testu obciążenia języka Visual Basic, jeśli wolisz.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. Z paska menu **wybierz pozycję Plik** > **nowego** > **projektu.**

   Zostanie otwarte okno dialogowe **Nowy projekt.**

3. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Zainstalowany** i **Visual C#,** a następnie wybierz kategorię **Testuj.** Wybierz szablon **Projektu testu wydajności sieci Web i testu obciążenia.**

   ![Szablon projektu testu wydajności i obciążenia sieci Web](media/web-perf-load-test-project-template.png)

4. Wprowadź nazwę projektu, jeśli nie chcesz używać nazwy domyślnej, a następnie wybierz przycisk **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wpisz test sieci **Web** w polu wyszukiwania, a następnie wybierz szablon Wydajność sieci Web i Test **obciążenia przestarzały] \[** dla języka C#. Wybierz pozycję **Dalej**.

4. Wprowadź nazwę projektu, jeśli nie chcesz używać nazwy domyślnej, a następnie wybierz pozycję **Utwórz**.

::: moniker-end

   Program Visual Studio tworzy projekt i wyświetla pliki w **Eksploratorze rozwiązań**. Projekt początkowo zawiera jeden plik testowy sieci web o nazwie *WebTest1.webtest*.

## <a name="add-a-load-test-to-the-project"></a>Dodawanie testu obciążenia do projektu

1. Z menu po kliknięciu prawym przyciskiem myszy lub menu kontekstowego węzła projektu w **Eksploratorze rozwiązań**wybierz polecenie **Dodaj** > **test obciążenia**.

   Zostanie otwarty **Kreator nowego testu obciążenia.**

1. Wybierz opcję **Lokalny test obciążenia,** a następnie wybierz pozycję **Dalej**. Więcej informacji na temat testowania obciążenia w chmurze można [znaleźć tutaj.](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts)

   ![Nowy kreator testu obciążenia — pierwsza strona](media/load-test-wizard-page-1.png)

1. Wybierz **przycisk Dalej,** aby przejść przez kreatora, aż dojdziesz **do dodaj testy do scenariusza testu obciążenia i edytować stronę miksu testowego.** Wybierz przycisk **Dodaj**.

   Zostanie otwarte okno dialogowe **Dodawanie testów.**

1. W obszarze **Dostępne testy**wybierz pozycję **WebTest1**, a następnie wybierz strzałkę w prawo, aby przenieść ją do pola **Wybrane testy.** Wybierz przycisk **OK.**

   ![Okno dialogowe Dodawanie testów](media/add-tests-dialog-box.png)

1. Powrót do **Kreatora nowego testu obciążenia**wybierz przycisk **Zakończ.**

   Test obciążenia jest dodawany do projektu, a plik testu obciążenia zostanie otwarty w oknie edytora.

## <a name="run-the-load-test"></a>Uruchom test obciążenia

Stworzyliśmy test obciążenia, który nie robi zbyt wiele, ale i tak go uruchommy.

Z menu po kliknięciu prawym przyciskiem myszy lub menu kontekstowego testu obciążenia otwartego w edytorze wybierz polecenie **Uruchom test obciążenia**.

![Uruchom test obciążenia menu](media/run-load-test.png)

Test obciążenia rozpoczyna pracę. Okno **Wyniki testu** pokazuje, że test jest w toku, a analizator testu obciążenia jest wyświetlany w oknie edytora. Po zakończeniu testu, który powinien wynosić pięć minut, jeśli zaakceptowano ustawienia domyślne, podsumowanie jest wyświetlane w edytorze. Można wybrać **wykresy,** **tabele**lub **szczegóły,** aby uzyskać różne informacje o wynikach testu obciążenia.

![Okno analizatora testów obciążenia](media/load-test-analyzer.png)

## <a name="next-steps"></a>Następne kroki

Teraz, po utworzeniu prostego projektu testu obciążenia, następnym krokiem jest skonfigurowanie scenariuszy, zestawów liczników i uruchamianie ustawień.

> [!div class="nextstepaction"]
> [Edytowanie ustawień testu](edit-load-tests.md)
