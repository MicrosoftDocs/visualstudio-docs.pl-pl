---
title: Tworzenie i Uruchamianie testów jednostkowych dla aplikacji platformy uniwersalnej systemu Windows
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 66a107fbd738bc26fdf608223ff43f958754e3ae
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065303"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Przewodnik: tworzenie i uruchamianie testów jednostkowych dla aplikacji platformy UWP

Program Visual Studio obejmuje obsługę aplikacji uniwersalnych platformy Windows (UWP) Testy jednostkowe. Obejmuje szablony projektów testów jednostkowych dla języka Visual C#, Visual Basic i Visual C++.

> [!TIP]
> Aby uzyskać więcej informacji na temat tworzenia aplikacji platformy uniwersalnej systemu Windows, zobacz [Rozpoczynanie pracy z aplikacjami platformy uniwersalnej systemu Windows](/windows/uwp/get-started/).

W poniższych procedurach opisano kroki, aby tworzenie, uruchamianie i debugowanie testów jednostkowych dla aplikacji platformy uniwersalnej systemu Windows.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Tworzenie projektu testu jednostkowego dla aplikacji platformy uniwersalnej systemu Windows

1.  Z **pliku** menu, wybierz **nowy projekt**.

     **Nowy projekt** Wyświetla okno dialogowe.

2.  W obszarze Szablony wybierz język programowania, który chcesz utworzyć testy jednostkowe w, a następnie wybierz skojarzone jednostki Windows Universal testowanie biblioteki. Na przykład wybrać **Visual C#** , następnie wybierz **Windows Universal**, a następnie wybierz **Biblioteka testów jednostkowych (Windows Universal)**.

3.  (Opcjonalnie) W **nazwa** polu tekstowym wprowadź nazwę, którego chcesz użyć dla projektu.

4.  (Opcjonalnie) Modyfikuj ścieżkę, w której chcesz utworzyć projekt, wprowadzając ją w **lokalizacji** pole tekstowe, lub wybierając **Przeglądaj** przycisku.

5.  (Opcjonalnie) W **rozwiązania** polu tekstowym, wprowadź nazwę, którego chcesz użyć dla rozwiązania.

6.  Pozostaw **Utwórz katalog rozwiązania** opcja wybrana i wybierz **OK** przycisku.

     ![Biblioteka testów jednostkowych dostosowanych do potrzeb](../test/media/unit_test_win8_1.png)

     **Eksplorator rozwiązań** jest wypełniana przy użyciu projektu testu jednostkowego platformy uniwersalnej systemu Windows, a Edytor kodu wyświetla domyślny test jednostki pod tytułem Testjednostki1.

     ![Nowy projekt testów jednostkowych dostosowanych do potrzeb](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Edytuj plik manifestu aplikacji platformy uniwersalnej systemu Windows projektu testu jednostkowego

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *Package.appxmanifest* pliku, a następnie wybierz **Otwórz**.

     **Manifest Designer** Wyświetla do edycji.

2.  W **Manifest Designer**, wybierz **możliwości** kartę.

3.  Na liście w obszarze **możliwości**, wybierz możliwości potrzebne do testu jednostkowego i kod jej ma mieć test. Na przykład wybierz **Internet** pole wyboru, jeśli testy jednostkowe i kod jest testowanie muszą mieć możliwość dostępu do Internetu.

    > [!NOTE]
    > Możliwości, którą wybierzesz powinien zawierać tylko funkcje, które są niezbędne dla testu jednostkowego działo poprawnie.

     ![Manifest testów jednostkowych](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Kodowanie testu jednostkowego dla aplikacji platformy uniwersalnej systemu Windows

W **Edytor kodu**, Edytuj test jednostkowy oraz Dodaj potwierdzenia i logikę wymagane dla testu.

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Aby skompilować rozwiązanie i uruchomić test jednostki za pomocą Eksploratora testów

1.  Na **testu** menu, wybierz **Windows**, a następnie wybierz **Eksplorator testów**.

     **Eksplorator testów** Wyświetla bez Twojego testu.

2.  Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

     Taki test jednostki znajduje się teraz.

    > [!NOTE]
    > Należy utworzyć rozwiązanie, które można zaktualizować listy testów jednostkowych w Eksploratorze testów.

3.  W **Eksploratora testów**, wybierz utworzony test jednostkowy.

    > [!TIP]
    > Test Explorer zawiera łącze do kodu źródłowego obok **źródło:**.

4.  Wybierz **uruchomić wszystkie**.

     ![Eksplorator testów jednostkowych &#45; uruchomić test jednostkowy](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

    > [!TIP]
    > Można wybrać jeden lub więcej testów wymienionych w Eksploratorze i kliknij prawym przyciskiem myszy i wybierz **Uruchom wybrane testy**.
    >
    > Ponadto istnieje możliwość **Debuguj wybrane testy**, **Otwórz Test**i użyj **właściwości** opcji.
    >
    > ![Eksplorator testów jednostkowych &#45; menu kontekstowe testów uni](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

    Przebiegi testów jednostkowych. Po zakończeniu **Eksploratora testów** Wyświetla stan badania, czas trwania i zawiera również link do źródła.

    ![Eksplorator testów jednostkowych &#45; testów zakończonych](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Zobacz także

- [Testowanie aplikacji platformy uniwersalnej systemu Windows z programem Visual Studio](../test/testing-store-apps-with-visual-studio.md)
- [Tworzenie i testowanie aplikacji platformy uniwersalnej systemu Windows](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
