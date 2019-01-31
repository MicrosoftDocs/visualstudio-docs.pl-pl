---
title: Tworzenie projektu testu jednostkowego
ms.date: 01/29/2019
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 813829e1e4024a38415cd9cef6da9fa7ca2ed87b
ms.sourcegitcommit: 9866740aec05d1a3a5dc3b4b6d2ceaeecbd3fc29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55424411"
---
# <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Testy jednostkowe dublowanie często struktury kodu w ramach testu. Na przykład projekt testu jednostkowego zostałyby utworzone dla każdego projektu kodu, w ramach produktu. Projekt testowy może znajdować się w tym samym rozwiązaniu, jak kod w środowisku produkcyjnym lub może być w oddzielnym rozwiązaniu. Może mieć wiele jednostek projekty testowe w rozwiązaniu.

> [!NOTE]
> Lokalizacja jednostek testów dla kodu natywnego i struktura projektu testowego może być inna niż strukturę, która jest opisane w tym artykule. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Aby utworzyć projekt testów jednostkowych

1. Na **pliku** menu, wybierz **New** , a następnie wybierz **projektu**. Lub naciśnij **Ctrl**+**Shift**+**N**.

2. W **nowy projekt** okna dialogowego rozwiń **zainstalowane** węzła, wybierz język, którego chcesz użyć dla projektu testowego, a następnie wybierz **testu**.

3. Aby użyć jednego z platform testów jednostkowych firmy Microsoft, wybierz opcję **projektu testu jednostkowego** z listy szablonów projektu. W przeciwnym razie wybierz szablon projektu jednostki środowiskiem testowym, którego chcesz użyć. Nadaj projektowi nazwę, a następnie wybierz **OK**.

4. W projekcie testu jednostki Dodaj odwołanie do testowanego kodu. Aby dodać odwołanie do projektu kodu, w tym samym rozwiązaniu:

   1. Wybierz projekt testowy w **Eksploratora rozwiązań**.

   2. Na **projektu** menu, wybierz **Dodaj odwołanie**.

   3. W **Menadżer odwołań**, wybierz opcję **rozwiązania** węźle **projektów**. Wybierz projekt kodu, aby przetestować, a następnie wybierz **OK**.

   Jeśli kod, który ma zostać przetestowana, jest w innej lokalizacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md) informacje dotyczące dodawania odwołania.

## <a name="next-steps"></a>Następne kroki

Zobacz jeden z następujących sekcji:

**Pisanie testów jednostkowych**

- [Kod testu jednostkowego](../test/unit-test-your-code.md)

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)

- [Użyj struktury MSTest w testach jednostkowych](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Uruchamianie testów jednostkowych**

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)