---
title: Dodawanie liczników do zestawów liczników do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b83d9c3624a4a268bfeba8a02b224fb9813ad7d1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594339"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Jak: Dodawanie liczników do zestawów liczników za pomocą Edytora testów obciążenia

Podczas tworzenia testu obciążenia za pomocą **Kreatora testów obciążenia**należy dodać początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji na temat korzystania z komputerów zdalnych w teście obciążenia, zobacz [Kontrolery testów i agenci testowi.](configure-test-agents-and-controllers-for-load-tests.md)

Liczniki można zarządzać w **Edytorze testów obciążenia**. Zestawy liczników, które są już dodane do testu są widoczne w węźle **Zestawy liczników** testu obciążenia. Po utworzeniu testu obciążenia można dodać nowe liczniki do istniejących zestawów liczników.

## <a name="to-add-counters-to-a-counter-set"></a>Aby dodać liczniki do zestawu liczników

1. Otwórz test obciążenia.

2. Rozwiń węzeł **Zestawy liczników.** Wszystkie zbiory liczników, które zostały dodane do testu obciążeniowego są widoczne.

    > [!NOTE]
    > Drzewo hierarchii testu obciążenia zawiera również węzeł **Uruchom ustawienia.** Ten węzeł zawiera węzeł **Mapowania zestawów liczników,** który pokazuje wszystkie komputery i zestawy liczników, które są mapowane na te komputery.

3. Kliknij prawym przyciskiem myszy istniejący zestaw **liczników,** a następnie wybierz polecenie Dodaj liczniki .

     Zostanie wyświetlone okno dialogowe **Pobranie liczników wydajności.**

4. W **Computer** polu kombi komputera wpisz nazwę komputera, na który chcesz zamapować. Alternatywnie wybierz jeden z komputerów z listy rozwijanej.

    > [!NOTE]
    > Ponieważ zestawy liczników muszą być mapowane na komputer przed zbieraniem danych o wydajności, należy określić komputer, na którym mają być zbierane dane o wydajności.

5. Wybierz **kategorię Wydajność,** aby filtrować kategorie liczników danych wydajności. Zostaną wyświetlenia dwie kolumny danych, z których można wybrać liczniki wydajności.

    > [!NOTE]
    > Niektóre kategorie liczników będą wymagać również wybrania wystąpienia. Na przykład jeśli wybierzesz licznik SQL, należy wybrać wystąpienie SQL, ponieważ może być więcej niż jedno wystąpienie SQL zainstalowane na komputerze docelowym.

6. Wybierz licznik i wystąpienie, które chcesz dodać do niestandardowego zestawu liczników.

     \-lub -

     Wybierz przycisk opcji **Wszystkie liczniki,** aby wybrać wszystkie dostępne liczniki.

7. Wybierz pozycję **OK**.

    > [!NOTE]
    > Istnieje również możliwość dodania liczników do zestawu liczników, wybierając istniejącą kategorię licznika lub licznika, wybierając kopię, a następnie wklejając ją do innego węzła zestawu liczników. Dodatkowe liczniki, które są kopiowane, ale nie są potrzebne, można usunąć.

## <a name="see-also"></a>Zobacz też

- [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
