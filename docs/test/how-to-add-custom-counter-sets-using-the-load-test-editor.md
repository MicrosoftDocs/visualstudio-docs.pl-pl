---
title: Dodaj niestandardowe zbiory liczników do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 7f916e469453d41321dd30404be6c0a6e4f5e56f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051487"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Porady: Dodawanie zbiorów liczników niestandardowych za pomocą edytora testu obciążenia

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, jest dodawany początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego.

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji dotyczących używania komputerów zdalnych w teście obciążenia, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Zarządzasz licznikami w **edytora testu obciążenia**. Zbiory liczników, które zostały już dodane do testu są widoczne w **zestawów liczników** węzeł testu obciążeniowego. Po utworzeniu Testu obciążenia, można dodać do niego nowe niestandardowe zbiory liczników.

![Niestandardowy zbiór liczników](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Aby dodać niestandardowy zbiór liczników do Testu obciążenia

1.  Otwórz test obciążenia.

2.  Rozwiń **zbiorów liczników** węzła. Wszystkie zbiory liczników, które zostały dodane do testu obciążeniowego są widoczne.

3.  Kliknij prawym przyciskiem myszy **zbiorów liczników** a następnie wybierz węzeł **Dodaj niestandardowy zbiór liczników**.

    > [!NOTE]
    > Zestaw liczników jest nadawana nazwa domyślna, takich jak **niestandardowe1**. Nazwę można zmienić za pomocą **właściwości** okna. Naciśnij klawisz **F4** do wyświetlenia **właściwości** okna.

4.  Aby dodać liczniki do Twojej liczników niestandardowych zestawu, kliknij prawym przyciskiem myszy nowy zbiór liczników, a następnie wybierz **Dodaj liczniki**. Aby uzyskać więcej informacji na temat sposobu dodawania liczników, zobacz [porady: Dodawanie liczników do zestawów liczników](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Istnieje także możliwość dodania niestandardowego zbioru liczników, klikając prawym przyciskiem myszy istniejący zbiór liczników, wybierając kopię i wklejając ją do węzła zbiory liczników. Dodatkowe liczniki, które są kopiowane, ale nie są potrzebne, mogą zostać usunięte. Można zmienić nazwę nowego zbioru liczników przy użyciu **właściwości** okna.

## <a name="see-also"></a>Zobacz także

- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)