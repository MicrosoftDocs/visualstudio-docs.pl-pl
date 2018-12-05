---
title: Utwórz projekt testu obciążenia i wydajności sieci web w programie Visual Studio
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: f2e0f06eddee4acd500e6bf4a8094dde4efc0d14
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896292"
---
# <a name="quickstart-create-a-load-test-project"></a>Szybki start: tworzenie projektu testu obciążeniowego

W tym 10-minutowy Przewodnik Szybki Start dowiesz się, jak utworzyć i uruchomić projekt testu obciążenia i wydajności sieci web w programie Visual Studio. Testy obciążenia wykonać wydajności sieci web lub testów jednostkowych, aby symulować wielu użytkownikom dostęp do serwera, w tym samym czasie.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Wymagania dotyczące oprogramowania

Projekty testów wydajności i obciążenia sieci Web są dostępne tylko w wersji Enterprise programu Visual Studio.

## <a name="install-the-load-testing-component"></a>Instalowanie składnika testowania obciążenia

Jeśli nie masz już wydajności sieci web ale zainstalowany składnik narzędzia do testowania obciążenia, należy go zainstalować za pomocą Instalatora programu Visual Studio.

1. Otwórz **Instalatora programu Visual Studio** z **Start** menu systemu Windows. Możesz również do niego dostęp w programie Visual Studio z **nowy projekt** okno dialogowe, lub wybierając **narzędzia** > **Pobierz narzędzia i funkcje** z paska menu.

1. W **Instalatora programu Visual Studio**, wybierz **poszczególne składniki** , a następnie przewiń w dół do **debugowanie i testowanie** sekcji. Wybierz **wydajności sieci Web i narzędzia do testowania obciążenia**.

   ![Składnik narzędzia do testowania obciążenia i wydajności sieci Web](media/web-perf-load-testing-tools-component.png)

1. Wybierz **Modyfikuj** przycisku.

   Zainstalowano wydajności sieci web i składnik narzędzia do testowania obciążenia.

## <a name="create-a-load-test-project"></a>Utwórz projekt testu obciążenia

W tej sekcji utworzymy projektu testu obciążeniowego języka C#. Można również utworzyć projekt testowy obciążenia Visual Basic, jeśli użytkownik sobie tego życzy.

1. Otwórz program Visual Studio, a następnie wybierz **pliku** > **New** > **projektu** z paska menu.

   **Nowy projekt** zostanie otwarte okno dialogowe.

1. W **nowy projekt** okna dialogowego rozwiń **zainstalowane** i **Visual C#**, a następnie wybierz pozycję **testu** kategorii. Wybierz **projekt testu obciążenia i wydajności sieci Web** szablonu.

   ![Szablon projektu testu wydajności sieci Web i obciążenia](media/web-perf-load-test-project-template.png)

1. Wprowadź nazwę dla projektu, jeśli nie chcesz użyć nazwy domyślnej, a następnie wybierz **OK**.

   Visual Studio tworzy projekt i wyświetla pliki w **Eksploratora rozwiązań**. Projekt zawiera początkowo jednego pliku testu sieci web o nazwie *WebTest1.webtest*.

## <a name="add-a-load-test-to-the-project"></a>Dodaj test obciążenia do projektu

1. Z menu kliknij prawym przyciskiem myszy lub z menu kontekstowe węzła projektu w **Eksploratora rozwiązań**, wybierz **Dodaj** > **testu obciążeniowego**.

   **Nowego kreatora testu obciążenia** zostanie otwarty.

1. Wybierz **testu obciążenia w środowisku lokalnym** opcji, a następnie wybierz **dalej**. Dowiedz się więcej na temat testowania obciążenia opartego na chmurze [tutaj](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts).

   ![Nowy Kreator testu obciążenia — pierwsza strona](media/load-test-wizard-page-1.png)

1. Wybierz **dalej** przechodzić przez kreatora aż **Dodaj testy do scenariusza testu obciążeniowego i Edytuj test mieszany** strony. Wybierz **Dodaj** przycisku.

   **Dodaj testy** zostanie otwarte okno dialogowe.

1. W obszarze **dostępne testy**, wybierz opcję **WebTest1**, a następnie wybierz strzałkę w prawo, aby przenieść go do **wybrane testy** pole. Wybierz **OK** przycisku.

   ![Dodawanie testów, okno dialogowe](media/add-tests-dialog-box.png)

1. Ponownie **nowego kreatora testu obciążenia**, wybierz **Zakończ** przycisku.

   Test obciążeniowy zostanie dodany do projektu, a plik testu obciążeniowego, który zostanie otwarty w oknie edytora.

## <a name="run-the-load-test"></a>Uruchom test obciążenia

Utworzyliśmy test obciążenia, który nie należy zrobić bardzo wiele, ale teraz Uruchom mimo to.

Wybierz z menu kliknij prawym przyciskiem myszy lub menu kontekstowego testu obciążenia, który jest otwarty w edytorze **Uruchom Test obciążenia**.

![Uruchom w menu Test obciążeniowy](media/run-load-test.png)

Test obciążeniowy zostanie uruchomiony. **Wyników testu** okno pokazuje, że test jest w toku i analizatora testu obciążenia jest wyświetlana w oknie edytora. Po zakończeniu testu, która powinna być pięć minut, jeśli możesz zaakceptować wartości domyślne, podsumowania jest wyświetlany w edytorze. Możesz wybrać **wykresów**, **tabel**, lub **szczegółów** uzyskać różne informacje o wynikach testu obciążenia.

![Okno analizator testu obciążenia](media/load-test-analyzer.png)

## <a name="next-steps"></a>Następne kroki

Teraz, po utworzeniu projektu testu obciążenia prosty, następnym krokiem jest konfiguracji scenariuszy, zbiorów liczników i parametrów uruchomieniowych.

> [!div class="nextstepaction"]
> [Edytuj ustawienia testu](edit-load-tests.md)
