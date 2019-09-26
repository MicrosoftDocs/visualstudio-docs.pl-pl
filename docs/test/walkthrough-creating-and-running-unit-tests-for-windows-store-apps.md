---
title: Tworzenie i Uruchamianie testów jednostkowych dla aplikacji platformy uniwersalnej systemu Windows
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: a123657e148e4c19c0fab1c1a9bf567ad2ea6fa8
ms.sourcegitcommit: 9a3972eb85de5443ac2bc03964c5a251c39b2921
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2019
ms.locfileid: "71301713"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla aplikacji platformy UWP

Program Visual Studio obejmuje obsługę aplikacji uniwersalnych platformy Windows (UWP) Testy jednostkowe. Program Visual Studio zawiera szablony projektów testów jednostkowych dla C#, Visual Basic C++i.

> [!TIP]
> Aby uzyskać więcej informacji na temat tworzenia aplikacji platformy uniwersalnej systemu Windows, zobacz [Rozpoczynanie pracy z aplikacjami platformy uniwersalnej systemu Windows](/windows/uwp/get-started/).

W poniższych procedurach opisano kroki tworzenia, uruchamiania i debugowania testów jednostkowych dla aplikacji platformy UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Tworzenie projektu testu jednostkowego dla aplikacji platformy uniwersalnej systemu Windows

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

2. W polu wyszukiwania na stronie **Utwórz nowy projekt** wprowadź **test jednostkowy**.

   Lista szablonów filtrów do tych dla testów jednostkowych.

3. Wybierz szablon **aplikacja testów jednostkowych (uniwersalna systemu Windows)** dla obu C# lub Visual Basic, a następnie wybierz przycisk **dalej**.

   ![Utwórz nową aplikację testową jednostkową platformy UWP w programie Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Opcjonalnie Zmień nazwę projektu lub rozwiązania i lokalizację, a następnie wybierz pozycję **Utwórz**.

5. Opcjonalnie Zmień wartość docelową i minimalną wersji platformy, a następnie wybierz przycisk **OK**.

Po wykonaniu tych kroków projekt testu jednostkowego zostanie utworzony i wyświetlony w Eksplorator rozwiązań.

![Projekt testu jednostkowego platformy UWP w Eksplorator rozwiązań](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. Z **pliku** menu, wybierz **nowy projekt**.

   **Nowy projekt** Wyświetla okno dialogowe.

2. W obszarze Szablony wybierz język programowania, który chcesz utworzyć testy jednostkowe w, a następnie wybierz skojarzone jednostki Windows Universal testowanie biblioteki. Na przykład wybrać **Visual C#** , następnie wybierz **Windows Universal**, a następnie wybierz **Biblioteka testów jednostkowych (Windows Universal)** .

3. (Opcjonalnie) W **nazwa** polu tekstowym wprowadź nazwę, którego chcesz użyć dla projektu.

4. (Opcjonalnie) Modyfikuj ścieżkę, w której chcesz utworzyć projekt, wprowadzając ją w **lokalizacji** pole tekstowe, lub wybierając **Przeglądaj** przycisku.

5. (Opcjonalnie) W **rozwiązania** polu tekstowym, wprowadź nazwę, którego chcesz użyć dla rozwiązania.

6. Pozostaw **Utwórz katalog rozwiązania** opcja wybrana i wybierz **OK** przycisku.

   ![Biblioteka testów jednostkowych dostosowanych do potrzeb](../test/media/unit_test_win8_1.png)

   **Eksplorator rozwiązań** jest wypełniana przy użyciu projektu testu jednostkowego platformy uniwersalnej systemu Windows, a Edytor kodu wyświetla domyślny test jednostki pod tytułem Testjednostki1.

   ![Nowy projekt testów jednostkowych dostosowanych do potrzeb](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Edytuj plik manifestu aplikacji platformy uniwersalnej systemu Windows projektu testu jednostkowego

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *Package.appxmanifest* pliku, a następnie wybierz **Otwórz**.

2. W **Manifest Designer**, wybierz **możliwości** kartę.

3. Na liście w obszarze **możliwości**, wybierz możliwości potrzebne do testu jednostkowego i kod jej ma mieć test. Na przykład wybierz **Internet** pole wyboru, jeśli testy jednostkowe i kod jest testowanie muszą mieć możliwość dostępu do Internetu.

   > [!NOTE]
   > Możliwości, którą wybierzesz powinien zawierać tylko funkcje, które są niezbędne dla testu jednostkowego działo poprawnie.

   ![Manifest testów jednostkowych](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Kodowanie testu jednostkowego dla aplikacji platformy uniwersalnej systemu Windows

W edytorze kodu Edytuj test jednostkowy i Dodaj potwierdzenia i logikę wymagane dla testu.

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

Aby skompilować rozwiązanie i uruchomić test jednostkowy przy użyciu Eksploratora testów:

1. Na **testu** menu, wybierz **Windows**, a następnie wybierz **Eksplorator testów**.

2. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

   Test jednostkowy jest teraz pokazywany w Eksploratorze testów.

   > [!NOTE]
   > Należy utworzyć rozwiązanie, które można zaktualizować listy testów jednostkowych w Eksploratorze testów.

3. W **Eksploratora testów**, wybierz utworzony test jednostkowy.

4. Wybierz **uruchomić wszystkie**.

   ![Eksplorator testów jednostkowych &#45; uruchomić test jednostkowy](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Można wybrać co najmniej jeden test jednostkowy wymieniony w Eksploratorze testów, a następnie kliknąć prawym przyciskiem myszy i wybrać polecenie **Uruchom wybrane testy**.
   >
   > Ponadto istnieje możliwość **Debuguj wybrane testy**, **Otwórz Test**i użyj **właściwości** opcji.
   >
   > ![Menu kontekstowe &#45; testu jednostkowego w Eksploratorze testów jednostkowych](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Przebiegi testów jednostkowych. Po zakończeniu Eksplorator testów wyświetla stan testu i czas, który upłynął, i udostępnia link do źródła.

   ![Eksplorator testów jednostkowych &#45; testów zakończonych](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Zobacz także

- [Testowanie aplikacji platformy uniwersalnej systemu Windows z programem Visual Studio](../test/unit-test-your-code.md)
- [Tworzenie i testowanie aplikacji platformy uniwersalnej systemu Windows](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)