---
title: 'Instrukcje: Tworzenie cieniowania tekstury w skali szarości | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 554717d59a42bed15b37379d3bf7a5c4da727e95
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664507"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Porady: tworzenie cieniowania tekstury skali szarości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób użycia projektanta programu do cieniowania i języka ukierunkowanego programu Graph (DGSL) do tworzenia cieniowania tekstury w skali szarości. Ten program do cieniowania modyfikuje wartość koloru RGB próbki tekstury, a następnie używa jej razem z niezmodyfikowaną wartością alfa, aby ustawić kolor końcowy.

## <a name="creating-a-grayscale-texture-shader"></a>Tworzenie cieniowania tekstury w skali szarości
 Można zaimplementować cieniowanie tekstury w skali szarości, modyfikując wartość koloru próbki tekstury przed jej zapisaniem w końcowym kolorze wyjściowym.

 Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

#### <a name="to-create-a-grayscale-texture-shader"></a>Aby utworzyć cieniowanie tekstury w skali szarości

1. Utwórz cieniowanie tekstury podstawowej, zgodnie z opisem w artykule [How to: Create a Basic cieniowanie tekstury](../designers/how-to-create-a-basic-texture-shader.md).

2. Odłącz Terminal **RGB** węzła **przykład tekstury** z terminalu **RGB** **końcowego węzła Color** . W obszarze tryb **wyboru** wybierz Terminal **RGB** w węźle **przykład tekstury** , a następnie wybierz polecenie **Przerwij linki**. Powoduje to powolne miejsce dla węzła, który jest dodawany w następnym kroku.

3. Dodaj do wykresu węzeł zmniejszający **nasycenie** . W **przyborniku**w obszarze **filtry**wybierz pozycję Zmniejsz **nasycenie** i przenieś ją na powierzchnię projektu.

4. Oblicz wartość skali odcieni szarości przy użyciu węzła Zmniejsz **nasycenie** . W trybie **wyboru** Przenieś Terminal **RGB** węzła **przykład tekstury** do terminalu **RGB** w węźle **denasycenie** .

   > [!NOTE]
   > Domyślnie **w pełni zmniejsza nasycenie** koloru i używa standardowych wag luminancji dla konwersji odcienie szarości. Można zmienić sposób zachowania węzła zmniejszania **nasycenia** , zmieniając wartość właściwości **luminancja** lub tylko częściowo denasycenie koloru wejściowego. Aby częściowo zmniejszać nasycenie koloru wejściowego, podaj wartość skalarną w zakresie [0, 1) do terminalu **procentowego** węzła zmniejszania **nasycenia** .

5. Połącz wartość koloru w skali szarości z kolorem końcowym. Przenieś Terminal **wyjściowy** węzła Zmniejsz **nasycenie** do terminalu **RGB** **końcowego węzła koloru** .

   Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i Podgląd cieniowania zastosowany do modułu.

> [!NOTE]
> Na tej ilustracji, płaszczyzna jest używana jako kształt podglądu i określono teksturę, aby lepiej zademonstrować efekt cieniowania.

 ![Graf cieniowania i podgląd jego efektu](../designers/media/digit-grayscale-effect.png "Cyfra — efekt w skali szarości")

 Niektóre kształty mogą zapewniać lepszy Podgląd niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat podglądu programów do cieniowania w projektancie cieniowania, zobacz [Projektant cieniowania](../designers/shader-designer.md)

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [instrukcje: eksportowanie](../designers/how-to-export-a-shader.md) [edytora obrazu](../designers/image-editor.md) programu do cieniowania [Designer](../designers/shader-designer.md) — [węzły projektanta](../designers/shader-designer-nodes.md) cieniowania
