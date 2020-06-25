---
title: Tworzenie projektu testu jednostkowego
ms.date: 01/29/2019
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ffa19fb9dc49d6286ef3f54c51d89043445f18ba
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288718"
---
# <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Testy jednostkowe często duplikują strukturę testowanego kodu. Na przykład projekt testu jednostkowego zostanie utworzony dla każdego projektu kodu w produkcie. Projekt testowy może być w tym samym rozwiązaniu co kod produkcyjny lub może znajdować się w osobnym rozwiązaniu. W rozwiązaniu można mieć wiele projektów testów jednostkowych.

> [!NOTE]
> Lokalizacja testów jednostkowych dla kodu natywnego i struktury projektu testowego może różnić się od struktury opisanej w tym artykule. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Aby utworzyć projekt testu jednostkowego

1. W menu **plik** wybierz polecenie **Nowy**  >  **projekt**lub naciśnij **klawisze CTRL** + **SHIFT** + **N**.

::: moniker range="vs-2017"

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowany** , wybierz język, który ma być używany dla projektu testowego, a następnie wybierz polecenie **Testuj**.

3. Wybierz szablon projektu dla środowiska testowego, którego chcesz użyć, na przykład **projekt testu MSTest** lub **projekt testowy nunit**. Nazwij projekt, a następnie wybierz **przycisk OK**.

   ![Szablony projektów testowych w programie Visual Studio 2017](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stronie **Tworzenie nowego projektu** wpisz **test jednostkowy** w polu wyszukiwania. Wybierz szablon projektu dla środowiska testowego, którego chcesz użyć, na przykład **projekt MSTest test** lub **projekt testowy nunit**, a następnie wybierz **dalej**.

   ![Szablony projektów testowych w programie Visual Studio 2019](media/vs-2019/test-project-templates.png)

3. Na stronie **Konfiguruj nowy projekt** wprowadź nazwę projektu, a następnie wybierz pozycję **Utwórz**.

::: moniker-end

4. W projekcie testów jednostkowych Dodaj odwołanie do testowanego kodu. Aby dodać odwołanie do projektu kodu w tym samym rozwiązaniu:

   1. Wybierz projekt testowy w **Eksplorator rozwiązań**.

   2. W menu **projekt** wybierz polecenie **Dodaj odwołanie**.

   3. W **Menedżerze odwołań**wybierz węzeł **rozwiązania** w obszarze **projekty**. Wybierz projekt kodu, który chcesz przetestować, a następnie wybierz przycisk **OK**.

   Jeśli kod, który ma zostać przetestowany, znajduje się w innej lokalizacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md) , aby uzyskać informacje na temat dodawania odwołania.

## <a name="next-steps"></a>Następne kroki

Zobacz jedną z następujących sekcji:

**Pisanie testów jednostkowych**

- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)

- [Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)

- [Używanie struktury MSTest w testach jednostkowych](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Uruchamianie testów jednostkowych**

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
