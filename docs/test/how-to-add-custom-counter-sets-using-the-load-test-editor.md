---
title: Dodawanie niestandardowych zestawów liczników na potrzeby testowania obciążenia
description: Podczas tworzenia testu obciążenia przy użyciu Kreator testu obciążeniowego należy dodać początkowy zestaw liczników. Dowiedz się, jak dodać niestandardowe zestawy liczników przy użyciu Edytor testu obciążeniowego.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ce34a4e30c9d612bd37afb61c354b7a4b5df7aed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966932"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Instrukcje: Dodawanie niestandardowych zestawów liczników przy użyciu Edytor testu obciążeniowego

Podczas tworzenia testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego** należy dodać początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego.

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji na temat używania maszyn zdalnych w teście obciążenia, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Zarządzasz licznikami w **Edytor testu obciążeniowego**. Zestawy liczników, które zostały już dodane do testu, są widoczne w węźle **zestawy liczników** testu obciążenia. Po utworzeniu Testu obciążenia, można dodać do niego nowe niestandardowe zbiory liczników.

![Niestandardowy zbiór liczników](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Aby dodać niestandardowy zbiór liczników do Testu obciążenia

1. Otwórz test obciążenia.

2. Rozwiń węzeł **zestawy liczników** . Wszystkie zbiory liczników, które zostały dodane do testu obciążeniowego są widoczne.

3. Kliknij prawym przyciskiem myszy węzeł **zestawy liczników** i wybierz polecenie **Dodaj niestandardowy zestaw liczników**.

    > [!NOTE]
    > Zestaw liczników otrzymuje nazwę domyślną, na przykład **Custom1**. Nazwę można zmienić przy użyciu okna **Właściwości** . Naciśnij klawisz **F4** , aby wyświetlić okno **Właściwości** .

4. Aby dodać liczniki do niestandardowego zestawu liczników, kliknij prawym przyciskiem myszy nowy zbiór liczników, a następnie wybierz polecenie **Dodaj liczniki**. Aby uzyskać więcej informacji na temat dodawania liczników, zobacz [How to: Add Counters to Counter Sets](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Istnieje także możliwość dodania niestandardowego zbioru liczników, klikając prawym przyciskiem myszy istniejący zbiór liczników, wybierając kopię i wklejając ją do węzła zbiory liczników. Dodatkowe liczniki, które są kopiowane, ale nie są potrzebne, mogą zostać usunięte. Nazwę nowego zestawu liczników można zmienić przy użyciu okna **Właściwości** .

## <a name="see-also"></a>Zobacz też

- [Określ zestawy liczników i reguły progowe dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Skonfiguruj ustawienia przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
