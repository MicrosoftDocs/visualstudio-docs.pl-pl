---
title: 'Porady: tworzenie cieniowania tekstury skali szarości'
description: Dowiedz się, jak używać projektanta programów do cieniowania i języka ukierunkowanego programu do cieniowania wykresów, aby utworzyć cieniowanie tekstury w skali szarości, które modyfikują kolor RGB przykładu tekstury.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4cde65d4540840470baad332b8092b5a410e14b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930996"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Instrukcje: tworzenie cieniowania tekstury skali szarości

W tym artykule pokazano, jak używać projektanta programu do cieniowania i języka ukierunkowanego programu Graph (DGSL) do tworzenia cieniowania tekstury w skali szarości. Ten program do cieniowania modyfikuje wartość koloru RGB próbki tekstury, a następnie używa jej razem z niezmodyfikowaną wartością alfa, aby ustawić kolor końcowy.

## <a name="create-a-grayscale-texture-shader"></a>Tworzenie cieniowania tekstury skali szarości

Można zaimplementować cieniowanie tekstury w skali szarości, modyfikując wartość koloru próbki tekstury przed jej zapisaniem w końcowym kolorze wyjściowym.

Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

1. Utwórz cieniowanie tekstury podstawowej, zgodnie z opisem w artykule [How to: Create a Basic cieniowanie tekstury](../designers/how-to-create-a-basic-texture-shader.md).

2. Odłącz Terminal **RGB** węzła **przykład tekstury** z terminalu **RGB** **końcowego węzła Color** . W obszarze tryb **wyboru** wybierz Terminal **RGB** w węźle **przykład tekstury** , a następnie wybierz polecenie **Przerwij linki**. Powoduje to powolne miejsce dla węzła, który jest dodawany w następnym kroku.

3. Dodaj do wykresu węzeł zmniejszający **nasycenie** . W **przyborniku** w obszarze **filtry** wybierz pozycję Zmniejsz **nasycenie** i przenieś ją na powierzchnię projektu.

4. Oblicz wartość skali odcieni szarości przy użyciu węzła Zmniejsz **nasycenie** . W trybie **wyboru** Przenieś Terminal **RGB** węzła **przykład tekstury** do terminalu **RGB** w węźle **denasycenie** .

    > [!NOTE]
    > Domyślnie **w pełni zmniejsza nasycenie** koloru i używa standardowych wag luminancji dla konwersji odcienie szarości. Można zmienić sposób zachowania węzła zmniejszania **nasycenia** , zmieniając wartość właściwości **luminancja** lub tylko częściowo denasycenie koloru wejściowego. Aby częściowo zmniejszać nasycenie koloru wejściowego, podaj wartość skalarną w zakresie [0, 1) do terminalu **procentowego** węzła zmniejszania **nasycenia** .

5. Połącz wartość koloru w skali szarości z kolorem końcowym. Przenieś Terminal **wyjściowy** węzła Zmniejsz **nasycenie** do terminalu **RGB** **końcowego węzła koloru** .

Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i Podgląd cieniowania zastosowany do modułu.

> [!NOTE]
> Na tej ilustracji, płaszczyzna jest używana jako kształt podglądu i określono teksturę, aby lepiej zademonstrować efekt cieniowania.

![Graf cieniowania i podgląd jego efektu](../designers/media/digit-grayscale-effect.png)

Niektóre kształty mogą zapewniać lepszy Podgląd niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat podglądu programów do cieniowania w projektancie cieniowania, zobacz [Projektant cieniowania](../designers/shader-designer.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: eksportowanie cieniowania](../designers/how-to-export-a-shader.md)
- [Edytor obrazów](../designers/image-editor.md)
- [Projektant programu do cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)
