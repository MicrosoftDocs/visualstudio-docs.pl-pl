---
title: Dodaj regułę progową do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ac4b542c7f9b557ad04ead05422f8c89cd4f909c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063373"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Porady: Dodawanie reguły progu za pomocą edytora testu obciążenia

Reguły progów w testach obciążenia porównanie wartości licznika wydajności za pomocą wartości stałej lub inną wartość licznika wydajności.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Aby dodać reguły progu

1.  Otwórz test obciążenia.

2.  W edytorze testu obciążenia, rozwiń węzeł **zbiorów liczników** węzła.

3.  Rozwiń jedno ze **kategorie liczników** w jednym ze zbiorów liczników. Na przykład, możesz wybrać **loadtest: Scenario**. Rozwiń węzeł.

4.  Kliknij prawym przyciskiem myszy jeden z liczników, na przykład **obciążenie użytkownikami**w obszarze **loadtest: Scenario**. Wybierz **Dodaj regułę progową**.

     **Dodaj regułę progową** zostanie wyświetlone okno dialogowe.

5.  Można wybrać spośród dwóch typów zasad: **Porównaj stałą** i **porównanie liczników**. Wybierz odpowiedni typ i ustaw wartości.

    > [!NOTE]
    > Ustaw **alertu, gdy nastąpi przekroczenie** właściwości **True** do wskazania przekroczenia progu to problemu, lub **False** do wskazywania objętych poniżej wartości progowej problem.

## <a name="see-also"></a>Zobacz także

- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
