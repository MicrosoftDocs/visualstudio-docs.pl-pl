---
title: Dodaj regułę progową na potrzeby testowania obciążenia
description: Dowiedz się więcej o regułach progowych w testach obciążenia, które porównują wartość licznika wydajności z wartością stałą lub inną wartością licznika wydajności.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efd601862de60c38991de5eb901de5b55605540a
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440223"
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
