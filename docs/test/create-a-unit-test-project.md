---
title: Tworzenie projektu testów jednostkowych
description: Dowiedz się, jak utworzyć projekt testu jednostkowego. Projekt testowy może być w tym samym rozwiązaniu co kod produkcyjny lub może znajdować się w osobnym rozwiązaniu.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8ca3cbe82bf4253e660ce69960570e40702c5512
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942363"
---
# <a name="create-a-unit-test-project"></a>Tworzenie projektu testów jednostkowych

Testy jednostkowe często duplikują strukturę testowanego kodu. Na przykład projekt testu jednostkowego zostanie utworzony dla każdego projektu kodu w produkcie. Projekt testowy może być w tym samym rozwiązaniu co kod produkcyjny lub może znajdować się w osobnym rozwiązaniu. W rozwiązaniu można mieć wiele projektów testów jednostkowych.

> [!NOTE]
> Lokalizacja testów jednostkowych dla kodu natywnego i struktury projektu testowego może różnić się od struktury opisanej w tym artykule. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Aby utworzyć projekt testu jednostkowego

1. W menu **plik** wybierz polecenie **Nowy**  >  **projekt** lub naciśnij **klawisze CTRL** + **SHIFT** + **N**.

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

   3. W **Menedżerze odwołań** wybierz węzeł **rozwiązania** w obszarze **projekty**. Wybierz projekt kodu, który chcesz przetestować, a następnie wybierz przycisk **OK**.

   Jeśli kod, który ma zostać przetestowany, znajduje się w innej lokalizacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md) , aby uzyskać informacje na temat dodawania odwołania.

## <a name="next-steps"></a>Następne kroki

Zobacz jedną z następujących sekcji:

**Pisanie testów jednostkowych**

- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)

- [Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)

- [Używanie struktury MSTest w testach jednostkowych](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Uruchamianie testów jednostkowych**

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
