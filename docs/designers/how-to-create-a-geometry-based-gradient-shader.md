---
title: 'Porady: tworzenie modułu cieniującego gradientu geometrycznego'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96326910a04294e30c410cc96bf9c600bfb3f17c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589460"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Instrukcje: tworzenie cieniowania gradientu geometrycznego

W tym artykule pokazano, jak utworzyć moduł cieniujący oparty na geometrii moduł cieniujący gradientu za pomocą projektanta modułu cieniującego i języka cieniowania wykresu skierowanego. Ten moduł cieniujący skaluje stałą wartość koloru RGB o wysokość każdego punktu obiektu w przestrzeni świata.

## <a name="create-a-geometry-based-gradient-shader"></a>Tworzenie cieniowania gradientu geometrycznego

Moduł cieniujący oparty na geometrii można zaimplementować, włączając położenie piksela do modułu cieniującego. W językach cieniowania piksel zawiera więcej informacji niż tylko jego kolor i lokalizację na ekranie 2D. Piksel — znany jako *fragment* w niektórych systemach — to zbiór wartości opisujących powierzchnię odpowiadającą pikselowi. Moduł cieniujący opisany w tym dokumencie wykorzystuje wysokość każdego piksela obiektu 3D w przestrzeni światowej, aby wpłynąć na końcowy kolor wyjściowy fragmentu.

Przed rozpoczęciem upewnij się, że są wyświetlane okno **Właściwości** i **Przybornik.**

1. Utwórz moduł cieniujący DGSL, z którym ma być działać. Aby uzyskać informacje dotyczące dodawania modułu cieniującego DGSL do projektu, zobacz sekcję Wprowadzenie w [Projektancie modułu cieniującego](../designers/shader-designer.md).

2. Odłącz węzeł **Kolor punktu** od **węzła Kolor końcowy.** Wybierz terminal **RGB** węzła **Kolor punktu,** a następnie wybierz pozycję **Przerwij łącza**. Dzięki temu miejsce na węzeł, który jest dodawany w następnym kroku.

3. Dodaj węzeł **Mnożenie** do wykresu. W **przyborniku**w obszarze **Matematyka**wybierz pozycję **Mnożenie** i przenieś ją na powierzchnię projektową.

4. Dodaj węzeł **Wektor maski** do wykresu. W **przyborniku**w obszarze **Narzędzie**wybierz pozycję **Maska Wektor** i przenieś ją na powierzchnię projektową.

5. Określ wartości maski dla **węzła Wektor maski.** W trybie **wyboru** wybierz węzeł **Wektor maski,** a następnie w oknie **Właściwości** ustaw właściwość **Zielony / Y** na **True**, a następnie ustaw właściwości Czerwony **/ X**, Niebieski **/ Z** i Alfa / **W** na **False**. W tym przykładzie właściwości **Red / X**, Green / **Y**i **Blue / Z** odpowiadają składnikom x, y i z **węzła Położenie świata,** a **Alfa / W** jest nieużywany. Ponieważ tylko **Zielony / Y** jest ustawiony na **True**, tylko składnik y wektora wejściowego pozostaje po jego zamaskowanie.

6. Dodaj węzeł **Pozycja świata** do wykresu. W **przyborniku**w obszarze **Stałe**wybierz **pozycję światową** i przesuń ją na powierzchnię projektową.

7. Zamaskuj pozycję przestrzeni światowej fragmentu. W trybie **wyboru** przenieś terminal **wyjściowy** **węzła Położenie światowe** do terminalu **wektorowego** **węzła Wektor maski.** To połączenie maskuje położenie fragmentu, aby zignorować komponenty x i z.

8. Pomnóż stałą koloru RGB przez zamaskowane położenie przestrzeni świata. Przenieś terminal **RGB** **węzła Kolor punktu** do terminalu **Y** **węzła Mnożenie,** a następnie przenieś terminal **wyjściowy** **węzła Wektor Maska** do terminalu **X** **węzła Mnożenie.** To połączenie skaluje wartość koloru o wysokość piksela w przestrzeni świata.

9. Połącz skalowany kolor z kolorem końcowym. Przenieś terminal **wyjściowy** węzła **Mnożenie** do terminalu **RGB** **węzła Kolor końcowy.**

Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i podgląd modułu cieniującego zastosowanego do kuli.

> [!NOTE]
> Na tej ilustracji kolor pomarańczowy jest określony, aby lepiej zademonstrować wpływ modułu cieniującego, ale ponieważ kształt podglądu nie ma pozycji w przestrzeni świata, moduł cieniujący nie może być w pełni wyświetlany w Projektancie modułu cieniującego. Moduł cieniujący musi być wyświetlany w rzeczywistej scenie, aby zademonstrować pełny efekt.

![Wykres modułu cieniującego i podgląd jego efektu](../designers/media/digit-gradient-effect-graph.png)

Niektóre kształty mogą zapewniać lepsze podglądy niektórych modułów cieniowania. Aby uzyskać informacje dotyczące wyświetlania podglądu modułów cieniujących w Projektancie modułów cieniujących, zobacz **Podgląd modułów cieniujących** w [Projektancie modułów cieniujących](../designers/shader-designer.md).

Na poniższej ilustracji przedstawiono moduł cieniujący opisany w tym dokumencie zastosowany do sceny 3D, która została zademonstrowana w [obszarze Jak: Model 3D terrain](../designers/how-to-model-3-d-terrain.md). Intensywność koloru wzrasta wraz z wysokością punktu na świecie.

![Efekt gradientu zastosowany do modelu terenu 3&#45;D](../designers/media/digit-gradient-effect-result.png)

Aby uzyskać więcej informacji na temat stosowania modułu cieniującego do modelu 3D, zobacz [Jak: Stosowanie modułu cieniującego do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: eksportowanie cieniowania](../designers/how-to-export-a-shader.md)
- [Jak: Model 3D terenu](../designers/how-to-model-3-d-terrain.md)
- [Instrukcje: tworzenie cieniowania tekstury skali szarości](../designers/how-to-create-a-grayscale-texture-shader.md)
- [Projektant modułu cieniującego](../designers/shader-designer.md)
- [Węzły projektanta modułu cieniującego](../designers/shader-designer-nodes.md)
