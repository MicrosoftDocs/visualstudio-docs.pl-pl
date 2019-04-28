---
title: Dodawanie liczników do zestawów liczników do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 004eff423874a07e2b49713eaed16eb1bf8be609
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979456"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Instrukcje: Dodawanie liczników do zestawów liczników za pomocą edytora testu obciążenia

Po utworzeniu testu obciążenia za pomocą **kreatora testu obciążenia**, jest dodawany początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji o sposobie używania komputerów zdalnych w teście obciążenia, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Zarządzasz licznikami w **edytora testu obciążenia**. Zbiory liczników, które zostały już dodane do testu są widoczne w **zestawów liczników** węzeł testu obciążeniowego. Po utworzeniu testu obciążenia, można dodać nowe liczniki do istniejących zestawów liczników.

## <a name="to-add-counters-to-a-counter-set"></a>Aby dodać liczniki do zestawu liczników

1. Otwórz test obciążenia.

2. Rozwiń **zbiorów liczników** węzła. Wszystkie zbiory liczników, które zostały dodane do testu obciążeniowego są widoczne.

    > [!NOTE]
    > Drzewo hierarchia test obciążenia zawiera także **parametrów uruchomieniowych** węzła. Ten węzeł zawiera **mapowaniach zbioru liczników** węzła, który przedstawia wszystkie komputery i zbiory liczników, które są mapowane na tych komputerach.

3. Kliknij prawym przyciskiem myszy istniejący zbiór liczników, a następnie wybierz **Dodaj liczniki**.

     **Wybierz liczniki wydajności** zostanie wyświetlone okno dialogowe.

4. W **komputera** rozwijane kombi wpisz nazwę komputera, którą chcesz zamapować do. Alternatywnie wybierz jeden z komputerów na liście rozwijanej.

    > [!NOTE]
    > Ponieważ zbiory liczników muszą być zamapowane na komputerze, zanim dane wydajności są zbierane, należy określić komputer, na którym można zbierać dane dotyczące wydajności.

5. Wybierz **kategorii wydajności** do filtrowania kategorii liczników wydajności, dane. Zostaną wyświetlone dwie kolumny danych, z którego ma zostać Wybierz liczniki wydajności.

    > [!NOTE]
    > Niektóre kategorie liczników wymaga również wybierz domyślne wystąpienie. Na przykład wybierzesz licznika SQL, należy wybranie wystąpienie serwera SQL, ponieważ może istnieć więcej niż jedno wystąpienie programu SQL Server zainstalowane na komputerze docelowym.

6. Wybierz licznik i wystąpienie, aby dodać do zestawu liczników niestandardowych.

     \- lub —

     Wybierz **wszystkie liczniki** przycisk radiowy, aby wybrać wszystkie dostępne liczniki.

7. Wybierz **OK**.

    > [!NOTE]
    > Istnieje również możliwość dodać liczniki do zbioru liczników, wybierając istniejący licznika lub kategoria licznika, wybierając kopię i wklejając ją do innego licznika Ustaw węzła. Dodatkowe liczniki, które są kopiowane, ale nie jest to konieczne, mogą zostać usunięte.

## <a name="see-also"></a>Zobacz także

- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)