---
title: Tworzenie i uruchamianie testów jednostkowych dla aplikacji platformy UWP
description: Dowiedz się więcej o obsłudze testów jednostkowych platforma uniwersalna systemu Windows aplikacji w programie Visual Studio. Program Visual Studio udostępnia szablony testów jednostkowych dla języków C#, Visual Basic i C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 52b7712c3e2e283dc92da3b920eccdcb0c312cd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948039"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla aplikacji platformy UWP

Program Visual Studio obejmuje obsługę aplikacji do testowania jednostek platforma uniwersalna systemu Windows (platformy UWP). Program Visual Studio zawiera szablony projektów testów jednostkowych dla języków C#, Visual Basic i C++.

> [!TIP]
> Aby uzyskać więcej informacji na temat opracowywania aplikacji platformy UWP, zobacz [wprowadzenie do aplikacji platformy UWP](/windows/uwp/get-started/).

W poniższych procedurach opisano kroki tworzenia, uruchamiania i debugowania testów jednostkowych dla aplikacji platformy UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Tworzenie projektu testu jednostkowego dla aplikacji platformy UWP

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

2. W polu wyszukiwania na stronie **Utwórz nowy projekt** wprowadź **test jednostkowy**.

   Lista szablonów filtrów do tych dla testów jednostkowych.

3. Wybierz szablon **aplikacja testów jednostkowych (uniwersalna systemu Windows)** dla języka C# lub Visual Basic, a następnie wybierz przycisk **dalej**.

   ![Utwórz nową aplikację testową jednostkową platformy UWP w programie Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Opcjonalnie Zmień nazwę projektu lub rozwiązania i lokalizację, a następnie wybierz pozycję **Utwórz**.

5. Opcjonalnie Zmień wartość docelową i minimalną wersji platformy, a następnie wybierz przycisk **OK**.

Po wykonaniu tych kroków projekt testu jednostkowego zostanie utworzony i wyświetlony w Eksplorator rozwiązań.

![Projekt testu jednostkowego platformy UWP w Eksplorator rozwiązań](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. Z menu **plik** wybierz pozycję **Nowy projekt**.

   Zostanie wyświetlone okno dialogowe **Nowy projekt** .

2. W obszarze szablony wybierz język programowania, w którym chcesz utworzyć testy jednostkowe, a następnie wybierz skojarzoną bibliotekę testów jednostki uniwersalnej systemu Windows. Na przykład wybierz pozycję **Visual C#** , a następnie wybierz pozycję **Windows Universal**, a następnie wybierz pozycję **Biblioteka testów jednostkowych (platforma uniwersalna systemu Windows)**.

3. Obowiązkowe W polu tekstowym **Nazwa** wprowadź nazwę, która ma być używana dla projektu.

4. Obowiązkowe Zmodyfikuj ścieżkę, w której chcesz utworzyć projekt, wprowadzając ją w polu tekstowym **Lokalizacja** lub wybierając przycisk **Przeglądaj** .

5. Obowiązkowe W polu tekstowym Nazwa **rozwiązania** wprowadź tę nazwę, która ma być używana dla Twojego rozwiązania.

6. Pozostaw wybraną opcję **Utwórz katalog dla rozwiązania** , a następnie wybierz przycisk **OK** .

   ![Dostosowana Biblioteka testów jednostkowych](../test/media/unit_test_win8_1.png)

   **Eksplorator rozwiązań** jest wypełniany projektem testów jednostkowych platformy UWP, a w edytorze kodu jest wyświetlany domyślny test jednostkowy o nazwie UnitTest1.

   ![Nowy dostosowany projekt testu jednostkowego](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Edytuj plik manifestu aplikacji platformy UWP projektu testów jednostkowych

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik *Package. appxmanifest* i wybierz polecenie **Otwórz**.

2. W **Projektancie manifestów** wybierz kartę **możliwości** .

3. Na liście w obszarze **możliwości** wybierz funkcje, które są potrzebne do testu jednostkowego, oraz kod, który ma być testowany. Na przykład zaznacz pole wyboru **Internet** , jeśli wymagane są testy jednostkowe i kod, który jest testowany, musi mieć możliwość uzyskania dostępu do Internetu.

   > [!NOTE]
   > Wybrane możliwości powinny zawierać tylko funkcje, które są niezbędne do poprawnego działania testu jednostkowego.

   ![Manifest testu jednostkowego](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Kod testu jednostkowego dla aplikacji platformy UWP

W edytorze kodu Edytuj test jednostkowy i Dodaj potwierdzenia i logikę wymagane dla testu.

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

Aby skompilować rozwiązanie i uruchomić test jednostkowy przy użyciu Eksploratora testów:

1. W menu **test** wybierz pozycję **Windows**, a następnie wybierz **Eksplorator testów**.

2. Z menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

   Test jednostkowy jest teraz pokazywany w Eksploratorze testów.

   > [!NOTE]
   > Należy skompilować rozwiązanie w celu zaktualizowania listy testów jednostkowych w Eksploratorze testów.

3. W **Eksploratorze testów** wybierz utworzony test jednostkowy.

4. Wybierz pozycję **Uruchom wszystkie**.

   ![Eksplorator testów jednostkowych &#45; uruchomić test jednostkowy](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Można wybrać co najmniej jeden test jednostkowy wymieniony w Eksploratorze testów, a następnie kliknąć prawym przyciskiem myszy i wybrać polecenie **Uruchom wybrane testy**.
   >
   > Ponadto możesz wybrać **debugowanie wybranych testów**, **otworzyć test** i użyć opcji **Właściwości** .
   >
   > ![Menu kontekstowe testu jednostkowego &#45;](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Uruchomienia testów jednostkowych. Po zakończeniu Eksplorator testów wyświetla stan testu i czas, który upłynął, i udostępnia link do źródła.

   ![Test jednostkowy Eksploratora testów &#45; zakończony](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Zobacz też

- [Testowanie aplikacji platformy UWP przy użyciu programu Visual Studio](../test/unit-test-your-code.md)
- [Kompilowanie i testowanie aplikacji platformy UWP](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
