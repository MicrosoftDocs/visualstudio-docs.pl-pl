---
title: Dodawanie reguły progowej do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d1389df0c307ad6ec65575fc7934e622928a0ca1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591635"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Jak: Dodawanie reguły progowej za pomocą edytora testów obciążenia

Reguły progowe w testach obciążenia porównują wartość licznika wydajności z wartością stałą lub inną wartością licznika wydajności.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Aby dodać regułę progową

1. Otwórz test obciążenia.

2. W Edytorze testów obciążenia rozwiń węzeł **Zestawy liczników.**

3. Rozwiń jedną z **kategorii liczników** w jednym z zestawów liczników. Na przykład można wybrać **LoadTest:Scenario**. Rozwiń węzeł.

4. Kliknij prawym przyciskiem myszy jeden z liczników, na przykład **Obciążenie użytkownika**, w obszarze **LoadTest:Scenario**. Wybierz **pozycję Dodaj regułę progu**.

     Zostanie wyświetlone okno dialogowe **Dodaj regułę progu.**

5. Możesz wybrać jeden z dwóch typów reguł: **Porównaj stały** i **Porównaj licznik**. Wybierz odpowiedni typ i ustaw wartości.

    > [!NOTE]
    > Ustaw **alert, jeśli over** właściwość **true,** aby wskazać, że przekroczenie progu jest problem lub **False,** aby wskazać, że spada poniżej progu jest problem.

## <a name="see-also"></a>Zobacz też

- [Analizowanie naruszeń reguł progowych](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
