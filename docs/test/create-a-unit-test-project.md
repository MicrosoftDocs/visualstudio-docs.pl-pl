---
title: Tworzenie projektu testu jednostkowego
ms.date: 01/29/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f04e999681899bb101dc0aeb70cc6f47094dc1d7
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483821"
---
# <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Testy jednostkowe dublowanie często struktury kodu w ramach testu. Na przykład projekt testu jednostkowego zostałyby utworzone dla każdego projektu kodu, w ramach produktu. Projekt testowy może znajdować się w tym samym rozwiązaniu, jak kod w środowisku produkcyjnym lub może być w oddzielnym rozwiązaniu. Może mieć wiele jednostek projekty testowe w rozwiązaniu.

> [!NOTE]
> Lokalizacja testów jednostkowych dla kodu natywnego i struktury projektu testowego może różnić się od struktury opisanej w tym artykule. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Aby utworzyć projekt testu jednostkowego

1. W menu **plik** wybierz polecenie **Nowy** > **projekt**lub naciśnij **klawisze CTRL**+**SHIFT**+**N**.

::: moniker range="vs-2017"

2. W **nowy projekt** okna dialogowego rozwiń **zainstalowane** węzła, wybierz język, którego chcesz użyć dla projektu testowego, a następnie wybierz **testu**.

3. Wybierz szablon projektu dla środowiska testowego, którego chcesz użyć, na przykład **projekt testu MSTest** lub **projekt testowy nunit**. Nazwij projekt, a następnie wybierz **przycisk OK**.

   ![Szablony projektów testowych w programie Visual Studio 2017](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stronie **Tworzenie nowego projektu** wpisz **test jednostkowy** w polu wyszukiwania. Wybierz szablon projektu dla środowiska testowego, którego chcesz użyć, na przykład **projekt MSTest test** lub **projekt testowy nunit**, a następnie wybierz **dalej**.

   ![Szablony projektów testowych w programie Visual Studio 2019](media/vs-2019/test-project-templates.png)

3. Na stronie **Konfiguruj nowy projekt** wprowadź nazwę projektu, a następnie wybierz pozycję **Utwórz**.

::: moniker-end

4. W projekcie testu jednostki Dodaj odwołanie do testowanego kodu. Aby dodać odwołanie do projektu kodu w tym samym rozwiązaniu:

   1. Wybierz projekt testowy w **Eksplorator rozwiązań**.

   2. Na **projektu** menu, wybierz **Dodaj odwołanie**.

   3. W **Menedżerze odwołań**wybierz węzeł **rozwiązania** w obszarze **projekty**. Wybierz projekt kodu, który chcesz przetestować, a następnie wybierz przycisk **OK**.

   Jeśli kod, który ma zostać przetestowany, znajduje się w innej lokalizacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md) , aby uzyskać informacje na temat dodawania odwołania.

## <a name="next-steps"></a>Następne kroki

Zobacz jeden z następujących sekcji:

**Pisanie testów jednostkowych**

- [Kod testu jednostkowego](../test/unit-test-your-code.md)

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)

- [Użyj struktury MSTest w testach jednostkowych](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Uruchamianie testów jednostkowych**

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)