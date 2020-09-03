---
title: Dodawanie liczników do zestawów liczników na potrzeby testowania obciążenia
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 754c88bd6dbe76736148718d2f1ad32888623c34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288380"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Instrukcje: Dodawanie liczników do zestawów liczników przy użyciu Edytor testu obciążeniowego

Podczas tworzenia testu obciążenia przy użyciu **Kreator testu obciążeniowego**należy dodać początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji na temat korzystania z maszyn zdalnych w teście obciążenia, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Zarządzasz licznikami w **Edytor testu obciążeniowego**. Zestawy liczników, które zostały już dodane do testu, są widoczne w węźle **zestawy liczników** testu obciążenia. Po utworzeniu testu obciążenia można dodać nowe liczniki do istniejących zestawów liczników.

## <a name="to-add-counters-to-a-counter-set"></a>Aby dodać liczniki do zestawu liczników

1. Otwórz test obciążenia.

2. Rozwiń węzeł **zestawy liczników** . Wszystkie zbiory liczników, które zostały dodane do testu obciążeniowego są widoczne.

    > [!NOTE]
    > Drzewo hierarchii testów obciążenia zawiera również węzeł **Parametry uruchomieniowe** . Ten węzeł zawiera węzeł **mapowania zestawów liczników** , który pokazuje wszystkie komputery i zestawy liczników, które są mapowane na te komputery.

3. Kliknij prawym przyciskiem myszy istniejący zestaw liczników, a następnie wybierz polecenie **Dodaj liczniki**.

     Zostanie wyświetlone okno dialogowe **liczniki wydajności pobierania** .

4. W polu kombi **komputer** wpisz nazwę komputera, na którym chcesz mapować. Alternatywnie wybierz jeden z komputerów na liście rozwijanej.

    > [!NOTE]
    > Ponieważ zestawy liczników muszą być mapowane na komputer przed zebraniem danych wydajności, należy określić komputer, na którym mają być zbierane dane dotyczące wydajności.

5. Wybierz **kategorię wydajności** , aby odfiltrować kategorie liczników danych wydajności. Zostaną wyświetlone dwie kolumny danych, z których mają zostać wybrane liczniki wydajności.

    > [!NOTE]
    > Niektóre kategorie liczników wymagają również wyboru wystąpienia. Na przykład w przypadku wybrania licznika SQL należy wybrać wystąpienie bazy danych SQL, ponieważ na komputerze docelowym może być zainstalowanych więcej niż jedno wystąpienie programu SQL Server.

6. Wybierz licznik i wystąpienie, które mają zostać dodane do niestandardowego zestawu liczników.

     \- oraz

     Wybierz przycisk radiowy **wszystkie liczniki** , aby wybrać wszystkie dostępne liczniki.

7. Wybierz przycisk **OK**.

    > [!NOTE]
    > Istnieje również możliwość dodania liczników do zestawu liczników przez wybranie istniejącej kategorii licznika lub licznika, wybranie opcji Kopiuj, a następnie wklejenie do innego węzła zestawu liczników. Dodatkowe liczniki, które są kopiowane, ale nie są potrzebne, mogą zostać usunięte.

## <a name="see-also"></a>Zobacz też

- [Określ zestawy liczników i reguły progowe dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Skonfiguruj ustawienia przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
