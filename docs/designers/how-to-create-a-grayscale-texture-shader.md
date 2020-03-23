---
title: 'Porady: tworzenie cieniowania tekstury skali szarości'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b74e956a74ff4c04dbc5a1c990fab708937d8f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112626"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Instrukcje: tworzenie cieniowania tekstury skali szarości

W tym artykule pokazano, jak utworzyć moduł cieniujący w skali szarości za pomocą projektanta modułu cieniującego i języka cieniowania wykresu kierowanego (DGSL). Ten moduł cieniujący modyfikuje wartość koloru RGB próbki tekstury, a następnie używa jej wraz z niezmodyfikowaną wartością alfa, aby ustawić ostateczny kolor.

## <a name="create-a-grayscale-texture-shader"></a>Tworzenie cieniowania tekstury skali szarości

Moduł cieniujący tekstury w skali szarości można zaimplementować, modyfikując wartość koloru próbki tekstury przed zapisaniem jej do końcowego koloru wyjściowego.

Przed rozpoczęciem upewnij się, że są wyświetlane okno **Właściwości** i **Przybornik.**

1. Utwórz podstawowy moduł cieniujący teksturę, zgodnie z opisem w [: Jak: Tworzenie podstawowego modułu cieniującego tekstury](../designers/how-to-create-a-basic-texture-shader.md).

2. Odłącz terminal **RGB** węzła **Próbka tekstury** od terminalu **RGB** **węzła Kolor końcowy.** W trybie **wyboru** wybierz terminal **RGB** **węzła Próbka tekstury,** a następnie wybierz polecenie **Przerwij łącza**. Dzięki temu miejsce na węzeł, który jest dodawany w następnym kroku.

3. Dodaj węzeł **Desaturate** do wykresu. W **przyborniku**w obszarze **Filtry**wybierz pozycję **Desaturate** i przenieś go na powierzchnię projektową.

4. Oblicz wartość skali szarości za pomocą **węzła Desaturate.** W trybie **wyboru** przenieś terminal **RGB** węzła **Próbka tekstury** do terminalu **RGB** **węzła Desaturate.**

    > [!NOTE]
    > Domyślnie węzeł **Desaturate** całkowicie desaturuje kolor wejściowy i używa standardowych wag luminancji do konwersji w skali szarości. Można zmienić zachowanie **węzła Desaturate,** zmieniając wartość właściwości **Luminance** lub tylko częściowo desaturating kolor wejściowy. Aby częściowo zdyskłać kolor wejściowy, podaj wartość skalarną w zakresie [0,1) do terminalu **Procent** **węzła Desaturate.**

5. Połącz wartość koloru w skali szarości z kolorem końcowym. Przenieś terminal **wyjściowy** **węzła Desaturate** do terminalu **RGB** węzła **Kolor końcowy.**

Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i podgląd modułu cieniującego zastosowanego do modułu.

> [!NOTE]
> Na tej ilustracji płaszczyzna jest używana jako kształt podglądu, a tekstura została określona, aby lepiej zademonstrować efekt modułu cieniującego.

![Wykres modułu cieniującego i podgląd jego efektu](../designers/media/digit-grayscale-effect.png)

Niektóre kształty mogą zapewniać lepsze podglądy niektórych modułów cieniowania. Aby uzyskać więcej informacji na temat podglądu modułów cieniujących w Projektancie modułów cieniujących, zobacz [Projektant modułu cieniującego](../designers/shader-designer.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: eksportowanie cieniowania](../designers/how-to-export-a-shader.md)
- [Edytor obrazów](../designers/image-editor.md)
- [Projektant modułu cieniującego](../designers/shader-designer.md)
- [Węzły projektanta modułu cieniującego](../designers/shader-designer-nodes.md)
