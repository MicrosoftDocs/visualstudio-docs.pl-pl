---
title: Tworzenie i uruchamianie testów jednostkowych dla aplikacji platformy uniwersalnej systemu Windows
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 4109f743caf7c62450591f78e90b92113fc4107e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568883"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Przewodnik: tworzenie i uruchamianie testów jednostkowych dla aplikacji platformy UWP

Program Visual Studio zawiera obsługę aplikacji do testowania jednostek platformy uniwersalnej systemu Windows (UWP). Program Visual Studio udostępnia szablony projektów testów jednostkowych dla języka C#, Visual Basic i C++.

> [!TIP]
> Aby uzyskać więcej informacji na temat tworzenia aplikacji platformy uniwersalnej systemu Windows, zobacz [Wprowadzenie do aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/get-started/).

W poniższych procedurach opisano kroki tworzenia, uruchamiania i debugowania testów jednostkowych dla aplikacji platformy uniwersalnej systemuśpiłka.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Tworzenie projektu testu jednostkowego dla aplikacji platformy uniwersalnej systemuśpiłka

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

2. W polu wyszukiwania na stronie **Utwórz nowy projekt** wprowadź **test jednostkowy**.

   Lista szablonów filtruje te do testowania jednostkowego.

3. Wybierz szablon **Aplikacji testu jednostkowego (Universal Windows)** dla języka C# lub Visual Basic, a następnie wybierz pozycję **Dalej**.

   ![Tworzenie nowej aplikacji do testowania jednostek platformy uniwersalnej systemu Wizjudy w programie Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Opcjonalnie zmień nazwę i lokalizację projektu lub rozwiązania, a następnie wybierz pozycję **Utwórz**.

5. Opcjonalnie zmień docelową i minimalną wersje platformy, a następnie wybierz **przycisk OK**.

Po wykonaniu tych kroków projekt testu jednostkowego jest tworzony i wyświetlany w Eksploratorze rozwiązań.

![Projekt testowy jednostki platformy uniwersalnej systemu Windows w Eksploratorze rozwiązań](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. Z menu **Plik** wybierz polecenie **Nowy projekt**.

   Zostanie wyświetlone okno dialogowe **Nowy projekt.**

2. W obszarze Szablony wybierz język programowania, w który chcesz utworzyć testy jednostkowe, a następnie wybierz skojarzoną bibliotekę testów jednostek systemu Windows Universal. Na przykład wybierz pozycję **Visual C#** , a następnie wybierz pozycję **Windows Universal**, a następnie wybierz pozycję **Biblioteka testów jednostek (universal Windows).**

3. (Opcjonalnie) W polach tekstowych **Nazwa** wprowadź nazwę, której chcesz użyć dla projektu.

4. (Opcjonalnie) Zmodyfikuj ścieżkę, w której chcesz utworzyć projekt, wprowadzając ją w polach tekstowych **Lokalizacja** lub wybierając przycisk **Przeglądaj.**

5. (Opcjonalnie) W polach tekstowych Nazwa **rozwiązania** wprowadź tę nazwę, której chcesz użyć dla rozwiązania.

6. Pozostaw zaznaczoną opcję **Utwórz katalog dla rozwiązania** i wybierz przycisk **OK.**

   ![Dostosowana biblioteka testowa jednostek](../test/media/unit_test_win8_1.png)

   **Eksplorator rozwiązań** jest wypełniany projektem testu jednostkowego platformy uniwersalnej systemu Windows, a edytor kodu wyświetla domyślny test jednostkowy zatytułowany UnitTest1.

   ![Nowy, dostosowany do indywidualnych potrzeb projekt testowy jednostki](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Edytowanie pliku manifestu aplikacji platformy uniwersalnej systemu wynajęciem aplikacji programu UNIWERSALNEGO projektu jednostki

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *Package.appxmanifest* i wybierz polecenie **Otwórz**.

2. W **projektancie manifestów**wybierz kartę **Możliwości.**

3. Na liście w obszarze **Możliwości**wybierz możliwości, które są potrzebne do testu jednostkowego i kod, który testuje. Na przykład zaznacz pole wyboru **Internet,** jeśli test jednostkowy wymaga i kod, który jest testowany, musi mieć możliwość dostępu do Internetu.

   > [!NOTE]
   > Wybrane funkcje powinny obejmować tylko funkcje, które są niezbędne do prawidłowego działania testu jednostkowego.

   ![Manifest testu jednostkowego](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Kod testu jednostkowego dla aplikacji platformy uniwersalnej systemu wyurzcie na platformy uniwersalne

W edytorze kodu edytuj test jednostkowy i dodaj potwierdzenia i logikę wymaganą dla testu.

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

Aby utworzyć rozwiązanie i uruchomić test jednostkowy przy użyciu Eksploratora testów:

1. W menu **Test** wybierz polecenie **Windows**, a następnie wybierz polecenie **Eksplorator testów**.

2. Z menu **Kompilacja** wybierz polecenie **Build Solution**.

   Test jednostkowy jest teraz wyświetlany w Eksploratorze testów.

   > [!NOTE]
   > Należy utworzyć rozwiązanie, aby zaktualizować listę testów jednostkowych w Eksploratorze testów.

3. W **Eksploratorze testów**wybierz utworzony test jednostkowy.

4. Wybierz **pozycję Uruchom wszystko**.

   ![Eksplorator testów jednostkowych &#45; uruchomieniu testu jednostkowego](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Można wybrać jeden lub więcej testów jednostkowych wymienionych w Eksploratorze testów, a następnie kliknąć prawym przyciskiem myszy i wybrać polecenie **Uruchom wybrane testy**.
   >
   > Ponadto można wybrać **debugowanie wybranych testów**, **Otwórz test**i użyć opcji **Właściwości.**
   >
   > ![Explorer testu jednostkowego &#45; menu kontekstowe testu jednostkowego](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Test jednostkowy jest uruchamiany. Po zakończeniu Eksplorator testów wyświetla stan testu i czas, który upłynął i udostępnia łącze do źródła.

   ![Ukończono &#45; test eksploratora testów jednostkowych](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Zobacz też

- [Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą programu Visual Studio](../test/unit-test-your-code.md)
- [Tworzenie i testowanie aplikacji platformy uniwersalnej systemu wytwórcza](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
