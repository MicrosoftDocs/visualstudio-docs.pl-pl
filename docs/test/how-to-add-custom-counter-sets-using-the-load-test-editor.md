---
title: Dodawanie niestandardowych zestawów liczników do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7438f657af2ba40fbda5afefbd8a12cc56a2a4c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114867"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Jak: Dodawanie niestandardowych zestawów liczników za pomocą Edytora testów obciążenia

Podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążenia**należy dodać początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego.

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji na temat używania komputerów zdalnych w teście obciążenia, zobacz [Kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

Liczniki można zarządzać w **Edytorze testów obciążenia**. Zestawy liczników, które są już dodane do testu są widoczne w węźle **Zestawy liczników** testu obciążenia. Po utworzeniu Testu obciążenia, można dodać do niego nowe niestandardowe zbiory liczników.

![Niestandardowy zbiór liczników](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Aby dodać niestandardowy zbiór liczników do Testu obciążenia

1. Otwórz test obciążenia.

2. Rozwiń węzeł **Zestawy liczników.** Wszystkie zbiory liczników, które zostały dodane do testu obciążeniowego są widoczne.

3. Kliknij prawym przyciskiem myszy węzeł **Zestawy liczników** i wybierz polecenie **Dodaj niestandardowy zestaw liczników**.

    > [!NOTE]
    > Zestaw liczników otrzymuje domyślną nazwę, taką jak **Custom1**. Nazwę można zmienić za pomocą okna **Właściwości.** Naciśnij **klawisz F4,** aby wyświetlić okno **Właściwości.**

4. Aby dodać liczniki do niestandardowego zestawu liczników, kliknij prawym przyciskiem myszy nowy zestaw **liczników,** a następnie wybierz polecenie Dodaj liczniki . Aby uzyskać więcej informacji na temat dodawania liczników, zobacz [Jak: Dodawanie liczników do zestawów liczników](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Istnieje także możliwość dodania niestandardowego zbioru liczników, klikając prawym przyciskiem myszy istniejący zbiór liczników, wybierając kopię i wklejając ją do węzła zbiory liczników. Dodatkowe liczniki, które są kopiowane, ale nie są potrzebne, mogą zostać usunięte. Nazwę nowego zestawu liczników można zmienić za pomocą okna **Właściwości.**

## <a name="see-also"></a>Zobacz też

- [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
