---
title: 'Porady: tworzenie podstawowego modułu cieniowanie Phong'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3059048f44524b9a838a8dfefc948ec4018dd05
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589490"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Instrukcje: tworzenie podstawowego cieniowania Phonga

W tym artykule pokazano, jak używać projektanta modułu cieniującego i języka cieniowania wykresu kierowanego (DGSL) do utworzenia modułu cieniującego oświetlenia, który implementuje klasyczny model oświetlenia Phong.

## <a name="the-phong-lighting-model"></a>Model oświetlenia Phong

Model oświetlenia Phong rozszerza model oświetlenia Lamberta o podświetlenie lustrzane, które symuluje odblaskowe właściwości powierzchni. Komponent lustrzany zapewnia dodatkowe oświetlenie z tych samych kierunkowych źródeł światła, które są używane w modelu oświetlenia Lamberta, ale jego wkład w końcowy kolor jest przetwarzany inaczej. Wyróżnianie specjaliny wpływa na każdą powierzchnię sceny w inny sposób, w zależności od relacji między kierunkiem widoku, kierunkiem źródeł światła i orientacją powierzchni. Jest to produkt koloru lustrzanego, mocy lustrzanej i orientacji powierzchni oraz koloru, intensywności i kierunku źródeł światła. Powierzchnie, które odbijają źródło światła bezpośrednio na widza, otrzymują maksymalny wkład lustrzany, a powierzchnie, które odzwierciedlają źródło światła od widza, nie otrzymują żadnego wkładu. W modelu oświetlenia Phong, jeden lub więcej elementów lustrzanych są łączone w celu określenia koloru i intensywności podświetlania lustrzanego dla każdego punktu na obiekcie, a następnie są dodawane do wyniku modelu oświetlenia Lamberta, aby uzyskać ostateczny kolor piksela .

Aby uzyskać więcej informacji na temat modelu oświetlenia Lambert, zobacz [Jak: Tworzenie podstawowego modułu cieniującego Lambert](../designers/how-to-create-a-basic-lambert-shader.md).

Przed rozpoczęciem upewnij się, że są wyświetlane okno **Właściwości** i **Przybornik.**

1. Utwórz moduł cieniujący Lambert, zgodnie z opisem w [jak: Tworzenie podstawowego modułu cieniującego Lamberta](../designers/how-to-create-a-basic-lambert-shader.md).

2. Odłącz węzeł **Lambert** od węzła **Kolor końcowy.** Wybierz terminal **RGB** węzła **Lambert,** a następnie wybierz pozycję **Przerwij łącza**. Dzięki temu miejsce na węzeł, który jest dodawany w następnym kroku.

3. Dodaj **węzeł** do wykresu. W **przyborniku**w obszarze **Matematyka**wybierz pozycję **Dodaj** i przenieś go na powierzchnię projektową.

4. Dodaj węzeł **specular** do wykresu. W **przyborniku**w obszarze **Narzędzie**wybierz opcję **Specular** i przenieś go na powierzchnię projektową.

5. Dodaj wkład spechularny. Przenieś terminal **wyjściowy** węzła **Specular** do terminalu **X** węzła **Dodaj,** a następnie przenieś terminal **wyjściowy** węzła **Lambert** do terminalu **Y** węzła **Dodaj.** Połączenia te łączą całkowity rozproszony i lustrzane proporcje kolorów dla piksela.

6. Połącz obliczoną wartość koloru z kolorem końcowym. Przenieś terminal **wyjściowy** węzła **Dodaj** do terminalu **RGB** **węzła Kolor końcowy.**

   Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i podgląd modułu cieniującego zastosowanego do modelu czajnika.

> [!NOTE]
> Aby lepiej zademonstrować wpływ modułu cieniującego na tej ilustracji, kolor pomarańczowy został określony za pomocą parametru **MaterialDiffuse** modułu cieniującego, a wykończenie o wyglądzie metalicznym zostało określone przy użyciu parametrów **MaterialSpecular** i **MaterialSpecularPower.** Aby uzyskać informacje o parametrach materiału, zobacz sekcję Podgląd modułów cieniujących w [Projektancie modułów cieniujących](../designers/shader-designer.md).

![Wykres modułu cieniującego i podgląd jego efektu](../designers/media/digit-lighting-graph.png)

Niektóre kształty mogą zapewniać lepsze podglądy niektórych modułów cieniowania. Aby uzyskać więcej informacji na temat wyświetlania podglądu modułów cieniujących w Projektancie modułów cieniujących, zobacz sekcję Podgląd modułów cieniujących w [Projektancie modułów cieniujących](../designers/shader-designer.md)

Na poniższej ilustracji przedstawiono moduł cieniujący opisany w tym dokumencie zastosowany do modelu 3D. **Właściwość MaterialSpecular** jest ustawiona na (1,00, 0,50, 0,20, 0,00), a jej **właściwość MaterialSpecularPower** jest ustawiona na 16.

> [!NOTE]
> **Właściwość MaterialSpecular** określa widoczne wykończenie materiału powierzchniowego. Powierzchnia o wysokim połysku, taka jak szkło lub plastik, ma zwykle kolor lustrzany, który jest jasnym odcieniem bieli. Metalowa powierzchnia ma tendencję do koloru lustrzanego, który jest zbliżony do jej rozproszonego koloru. Satynowa powierzchnia ma zwykle kolor lustrzany, który jest ciemnym odcieniem szarości.
>
> **Właściwość MaterialSpecularPower** określa, jak intensywne są światła lustrzane. Wysokie moce lustrzane symulują nudniejsze, bardziej zlokalizowane pasemka. Bardzo niskie moce lustrzane symulują intensywne, zamiatanie podkreśla, które mogą przesycą i ukryć kolor całej powierzchni.

![Oświetlenie Phong zastosowane do modelu](../designers/media/digit-lighting-model.png)

Aby uzyskać więcej informacji na temat stosowania modułu cieniującego do modelu 3D, zobacz [Jak: Stosowanie modułu cieniującego do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: eksportowanie cieniowania](../designers/how-to-export-a-shader.md)
- [Instrukcje: tworzenie podstawowego cieniowania Lamberta](../designers/how-to-create-a-basic-lambert-shader.md)
- [Projektant modułu cieniującego](../designers/shader-designer.md)
- [Węzły projektanta modułu cieniującego](../designers/shader-designer-nodes.md)
