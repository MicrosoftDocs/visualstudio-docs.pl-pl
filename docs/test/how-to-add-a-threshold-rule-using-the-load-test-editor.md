---
title: Dodaj regułę progową na potrzeby testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4ecec4826966205d849c07169da954198d687696
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644427"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Instrukcje: Dodawanie reguły progu za pomocą edytora testu obciążenia

Reguły progowe w testach obciążenia porównują wartość licznika wydajności z wartością stałą lub inną wartością licznika wydajności.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Aby dodać regułę progową

1. Otwórz test obciążenia.

2. W Edytor testu obciążeniowego rozwiń węzeł **zestawy liczników** .

3. Rozwiń jedną z **kategorii licznika** w jednym z zestawów liczników. Na przykład możesz wybrać pozycję **LoadTest: scenariusz**. Rozwiń węzeł.

4. Kliknij prawym przyciskiem myszy jeden z liczników, na przykład **obciążenie użytkownikami**, w obszarze **LoadTest: scenariusz**. Wybierz pozycję **Dodaj regułę progową**.

     Zostanie wyświetlone okno dialogowe **Dodaj regułę progową** .

5. Można wybrać jedną z dwóch typów reguł: **PORÓWNAJ stałą** i **PORÓWNAJ licznik**. Wybierz odpowiedni typ i ustaw wartości.

    > [!NOTE]
    > Ustaw **alert, jeśli właściwość over** ma **wartość true** , aby wskazać, że przekroczenie progu jest problemem, lub **wartość false** , aby wskazać, że poniżej progu jest problem.

## <a name="see-also"></a>Zobacz także

- [Analizowanie naruszeń reguł progu](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Określ zestawy liczników i reguły progowe dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
