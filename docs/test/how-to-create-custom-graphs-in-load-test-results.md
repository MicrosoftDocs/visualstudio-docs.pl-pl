---
title: 'Porady: tworzenie wykresów niestandardowych w wynikach testów obciążenia'
description: Dowiedz się, jak projektować wykresy, które wyświetlają określone informacje na temat wyników testów obciążenia albo gdy test obciążenia jest uruchomiony lub po zakończeniu działania.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c003fc5d6573dfdd88ec85ea37fbb10f80c94484
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441042"
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>Instrukcje: Tworzenie niestandardowych wykresów w wynikach testu obciążenia

Można zaprojektować wykresy, które wyświetlają określone informacje na temat wyników testu obciążenia. Wykres niestandardowy można zaprojektować, określając liczniki testów obciążenia, które będą wyświetlane na wykresie.

Poniższą procedurę można wykonać w czasie, gdy test obciążenia jest uruchomiony lub po zakończeniu działania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-load-test-results-graph"></a>Aby utworzyć wykres wyników niestandardowego testu obciążenia

1. Na pasku narzędzi **testu obciążenia** wybierz pozycję **Dodaj nowy Graf**.

     \- oraz

     W **analizatorze testu obciążenia** kliknij prawym przyciskiem myszy w panelu **liczniki** lub w grafie, a następnie wybierz polecenie **Dodaj wykres**.

     Zostanie wyświetlone okno dialogowe **wprowadzanie nazwy grafu** .

2. W obszarze **Nazwa wykresu** wpisz nazwę wykresu, a następnie wybierz **przycisk OK**.

     Nowy wykres zostanie wyświetlony w **analizatorze testu obciążenia**. Pojawia się w aktualnie wybranym panelu wykresu; zastępuje wykres, który był wyświetlany w tym panelu.

3. Dostosuj nowy wykres, dodając liczniki. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Instrukcje: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
