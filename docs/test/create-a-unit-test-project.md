---
title: Tworzenie projektu testu jednostkowego
ms.date: 01/29/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 313083090c94c94f4e196e87f3bf6cf6df36e118
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565256"
---
# <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Testy jednostkowe często dublują strukturę testowego kodu. Na przykład projekt testu jednostkowego zostanie utworzony dla każdego projektu kodu w produkcie. Projekt testowy może być w tym samym rozwiązaniu co kod produkcyjny lub może znajdować się w osobnym rozwiązaniu. W rozwiązaniu może być dostępnych wiele projektów testów jednostkowych.

> [!NOTE]
> Lokalizacja testów jednostkowych dla kodu macierzystego i struktury projektu testowego może być inna niż struktura opisana w tym artykule. Aby uzyskać więcej informacji, zobacz [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Aby utworzyć projekt testu jednostkowego

1. W menu **Plik** wybierz polecenie **Nowy** > **projekt**lub naciśnij **klawisze Ctrl**+**Shift**+**N**.

::: moniker range="vs-2017"

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Zainstalowany,** wybierz język, którego chcesz użyć w projekcie testowym, a następnie wybierz pozycję **Testuj**.

3. Wybierz szablon projektu dla struktury testów, której chcesz użyć, na przykład **MSTest Test Project** lub **NUnit Test Project**. Nazwij projekt, a następnie wybierz przycisk **OK**.

   ![Testowanie szablonów projektów w programie Visual Studio 2017](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stronie **Tworzenie nowego projektu** wpisz test **jednostkowy** w polu wyszukiwania. Wybierz szablon projektu dla struktury testów, której chcesz użyć, na przykład **MSTest Test Project** lub **NUnit Test Project**, a następnie wybierz pozycję **Dalej**.

   ![Testowanie szablonów projektów w programie Visual Studio 2019](media/vs-2019/test-project-templates.png)

3. Na stronie **Konfigurowanie nowego projektu** wprowadź nazwę projektu, a następnie wybierz pozycję **Utwórz**.

::: moniker-end

4. W projekcie testu jednostkowego dodaj odwołanie do kodu w ramach testu. Aby dodać odwołanie do projektu kodu w tym samym rozwiązaniu:

   1. Wybierz projekt testowy w **Eksploratorze rozwiązań**.

   2. W menu **Projekt** wybierz polecenie **Dodaj odwołanie**.

   3. W **Menedżerze odwołań**wybierz węzeł **Rozwiązanie** w obszarze **Projekty**. Wybierz projekt kodu, który chcesz przetestować, a następnie wybierz **przycisk OK**.

   Jeśli kod, który chcesz przetestować znajduje się w innej lokalizacji, zobacz [Zarządzanie odwołaniami w projekcie,](../ide/managing-references-in-a-project.md) aby uzyskać informacje na temat dodawania odwołania.

## <a name="next-steps"></a>Następne kroki

Zobacz jedną z następujących sekcji:

**Pisanie testów jednostkowych**

- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)

- [Użyj struktury MSTest w testach jednostkowych](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Uruchamianie testów jednostkowych**

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
