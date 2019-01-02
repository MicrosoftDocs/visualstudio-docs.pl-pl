---
title: Tworzenie projektu testu jednostkowego
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8b3b3f8af1dbc2cfd745a56238694cd19cc1f16d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824941"
---
# <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Testy jednostkowe dublowanie często struktury kodu w ramach testu. Na przykład projekt testu jednostkowego zostałyby utworzone dla każdego projektu kodu, w ramach produktu. Projekt testowy może znajdować się w tym samym rozwiązaniu, jak kod w środowisku produkcyjnym lub może być w oddzielnym rozwiązaniu. Może mieć wiele jednostek projekty testowe w rozwiązaniu.

> [!NOTE]
> Lokalizacja jednostek testów dla kodu natywnego i struktura projektu testowego może być inna niż strukturę, która jest opisane w tym temacie. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Aby utworzyć projekt testów jednostkowych:

1.  Na **pliku** menu, wybierz **New** , a następnie wybierz **projektu** (klawiatura **Ctrl**+**Shift** + **N**).

2.  W **nowy projekt** okna dialogowego rozwiń **zainstalowane** węzła, wybierz język, którego chcesz użyć dla projektu testowego, a następnie wybierz **testu**.

3.  Aby użyć jednego z platform testów jednostkowych firmy Microsoft, wybierz opcję **projektu testu jednostkowego** z listy szablonów projektu. W przeciwnym razie wybierz szablon projektu jednostki środowiskiem testowym, którego chcesz użyć. Aby przetestować projekt kont w naszym przykładzie, czy nazwa projektu **AccountsTests**.

4.  W projekcie testu jednostki Dodaj odwołanie do testowanego kodu.  Oto jak utworzyć odwołanie do projektu kodu w tym samym rozwiązaniu:

    1.  Wybierz projekt w **Eksploratora rozwiązań**.

    2.  Na **projektu** menu, wybierz **Dodaj odwołanie**.

    3.  W **Menadżer odwołań** po otwarciu okna dialogowego **rozwiązania** węzeł i wybierz polecenie **projektów**. Sprawdź nazwę projektu kodu, a następnie zamknij okno dialogowe.

5.  Jeśli kod, który ma zostać przetestowana, jest w innej lokalizacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md) informacje dotyczące dodawania odwołania.

## <a name="next-steps"></a>Następne kroki

 Zobacz jeden z następujących sekcji:

**Pisanie testów jednostkowych**

- [Kod testu jednostkowego](../test/unit-test-your-code.md)

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)

- [Użyj struktury MSTest w testach jednostkowych](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Uruchamianie testów jednostkowych**

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)