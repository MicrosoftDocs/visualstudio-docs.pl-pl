---
title: 'Instrukcje: Tworzenie cieniowania tekstury skali szarości'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a8e0295864986ad5cfae2f304f5b0f802f2fb12
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924305"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Instrukcje: Tworzenie cieniowania tekstury skali szarości

W tym artykule pokazano, jak używać projektanta programu do cieniowania i języka ukierunkowanego programu Graph (DGSL) do tworzenia cieniowania tekstury w skali szarości. Ten program do cieniowania modyfikuje wartość koloru RGB próbki tekstury, a następnie używa jej razem z niezmodyfikowaną wartością alfa, aby ustawić kolor końcowy.

## <a name="create-a-grayscale-texture-shader"></a>Tworzenie cieniowania tekstury skali szarości

Można zaimplementować cieniowanie tekstury w skali szarości, modyfikując wartość koloru próbki tekstury przed jej zapisaniem w końcowym kolorze wyjściowym.

Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

1. Utwórz cieniowanie tekstury w warstwie Podstawowa, zgodnie [z opisem w temacie How to: Utwórz program do cieniowania](../designers/how-to-create-a-basic-texture-shader.md)tekstury podstawowej.

2. Odłącz Terminal **RGB** węzła **przykład tekstury** z terminalu **RGB** **końcowego węzła Color** . W obszarze tryb **wyboru** wybierz Terminal **RGB** w węźle **przykład tekstury** , a następnie wybierz polecenie **Przerwij linki**. Powoduje to powolne miejsce dla węzła, który jest dodawany w następnym kroku.

3. Dodaj do wykresu węzeł zmniejszający nasycenie. W **przyborniku**w obszarze **filtry**wybierz pozycję Zmniejsz **nasycenie** i przenieś ją na powierzchnię projektu.

4. Oblicz wartość skali odcieni szarości przy użyciu węzła Zmniejsz nasycenie. W trybie **wyboru** Przenieś Terminal **RGB** węzła **przykład tekstury** do terminalu **RGB** w węźle denasycenie.

    > [!NOTE]
    > Domyślnie w pełni zmniejsza nasycenie koloru i używa standardowych wag luminancji dla konwersji odcienie szarości. Można zmienić sposób zachowania węzła zmniejszania nasycenia, zmieniając wartość właściwości luminancja lub tylko częściowo denasycenie koloru wejściowego. Aby częściowo zmniejszać nasycenie koloru wejściowego, podaj wartość skalarną w zakresie [0, 1) do terminalu **procentowego** węzła zmniejszania **nasycenia** .

5. Połącz wartość koloru w skali szarości z kolorem końcowym. Przenieś Terminal **wyjściowy** węzła Zmniejsz nasycenie do terminalu **RGB** **końcowego węzła koloru** .

Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i Podgląd cieniowania zastosowany do modułu.

> [!NOTE]
> Na tej ilustracji, płaszczyzna jest używana jako kształt podglądu i określono teksturę, aby lepiej zademonstrować efekt cieniowania.

![Graf cieniowania i podgląd jego efektu](../designers/media/digit-grayscale-effect.png)

Niektóre kształty mogą zapewniać lepszy Podgląd niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat podglądu programów do cieniowania w projektancie cieniowania, zobacz [Projektant cieniowania](../designers/shader-designer.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: Eksportowanie programu do cieniowania](../designers/how-to-export-a-shader.md)
- [Edytor obrazów](../designers/image-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)