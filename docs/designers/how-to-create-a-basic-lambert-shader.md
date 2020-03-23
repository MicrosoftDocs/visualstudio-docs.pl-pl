---
title: 'Porady: tworzenie podstawowego modułu cieniującego Lamberta'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d78bc6e1b384f339d80e09fec81d42c1ab8ed103
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589503"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Instrukcje: tworzenie podstawowego cieniowania Lamberta

W tym artykule pokazano, jak używać projektanta modułu cieniującego i języka cieniowania wykresu kierowanego (DGSL) do utworzenia modułu cieniującego oświetlenia, który implementuje klasyczny model oświetlenia Lamberta.

## <a name="the-lambert-lighting-model"></a>Model oświetlenia Lamberta

Model oświetlenia Lamberta wykorzystuje oświetlenie otoczenia i kierunkowe, aby zacienić obiekty w scenie 3D. Elementy otoczenia zapewniają podstawowy poziom oświetlenia w scenie 3D. Elementy kierunkowe zapewniają dodatkowe oświetlenie ze źródeł światła kierunkowego (daleko). Oświetlenie otoczenia wpływa równomiernie na wszystkie powierzchnie sceny, niezależnie od ich orientacji. Dla danej powierzchni jest to produkt koloru otoczenia powierzchni oraz koloru i intensywności oświetlenia otoczenia w scenie. Oświetlenie kierunkowe wpływa na każdą powierzchnię sceny w różny sposób, w zależności od orientacji powierzchni w stosunku do kierunku źródła światła. Jest to produkt rozproszonego koloru i orientacji powierzchni oraz koloru, intensywności i kierunku źródeł światła. Powierzchnie skierowane bezpośrednio w kierunku źródła światła otrzymują maksymalny wkład, a powierzchnie, które są bezpośrednio skierowane bezpośrednio, nie otrzymują żadnego wkładu. W modelu oświetlenia Lambert komponent otoczenia i jeden lub więcej komponentów kierunkowych są łączone w celu określenia całkowitego wkładu kolorów rozproszonych dla każdego punktu na obiekcie.

Przed rozpoczęciem upewnij się, że są wyświetlane okno **Właściwości** i **Przybornik.**

1. Utwórz moduł cieniujący DGSL, z którym ma być działać. Aby uzyskać informacje dotyczące dodawania modułu cieniującego DGSL do projektu, zobacz sekcję Wprowadzenie w [Projektancie modułu cieniującego](../designers/shader-designer.md).

2. Odłącz węzeł **Kolor punktu** od **węzła Kolor końcowy.** Wybierz terminal **RGB** węzła **Kolor punktu,** a następnie wybierz pozycję **Przerwij łącza**. Pozostaw podłączony terminal **Alpha.**

3. Dodaj węzeł **Lambert** do wykresu. W **przyborniku**, w obszarze **Narzędzie**wybierz **Lambert** i przesuń go na powierzchnię projektową. Węzeł lambert oblicza całkowity rozproszony wkład kolorów piksela na podstawie parametrów oświetlenia otoczenia i rozproszonego.

4. Połącz węzeł **Kolor punktu** z węzłem **Lambert.** W trybie **wyboru** przenieś terminal **RGB** węzła **Kolor punktu** do terminalu **Kolor rozproszony** **węzła Lambert.** To połączenie zapewnia węzłowi lamberta interpolowany rozproszony kolor piksela.

5. Połącz obliczoną wartość koloru z kolorem końcowym. Przenieś terminal **wyjściowy** węzła **Lambert** do terminalu **RGB** **węzła Kolor końcowy.**

   Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i podgląd modułu cieniującego zastosowanego do modelu czajnika.

> [!NOTE]
> Aby lepiej zademonstrować wpływ modułu cieniującego na tej ilustracji, kolor pomarańczowy został określony za pomocą parametru **MaterialDiffuse** modułu cieniującego. Gra lub aplikacja może użyć tego parametru, aby podać unikatową wartość koloru dla każdego obiektu. Aby uzyskać informacje o parametrach materiału, zobacz sekcję Podgląd modułów cieniujących w [Projektancie modułów cieniujących](../designers/shader-designer.md).

![Wykres modułu cieniującego i podgląd jego efektu.](../designers/media/digit-lambert-effect-graph.png)

Niektóre kształty mogą zapewniać lepsze podglądy niektórych modułów cieniowania. Aby uzyskać więcej informacji na temat wyświetlania podglądu modułów cieniujących w Projektancie modułów cieniujących, zobacz sekcję Podgląd modułów cieniujących w [Projektancie modułów cieniujących](../designers/shader-designer.md).

Na poniższej ilustracji przedstawiono moduł cieniujący opisany w tym dokumencie zastosowany do modelu 3D.

![Oświetlenie Lamberta zastosowane do modelu.](../designers/media/digit-lambert-effect-result.png)

Aby uzyskać więcej informacji na temat stosowania modułu cieniującego do modelu 3D, zobacz [Jak: Stosowanie modułu cieniującego do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz też

- [Jak: Stosowanie modułu cieniującego do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Jak: Eksportowanie modułu cieniującego](../designers/how-to-export-a-shader.md)
- [Jak: Tworzenie podstawowego modułu cieniującego Phong](../designers/how-to-create-a-basic-phong-shader.md)
- [Projektant modułu cieniującego](../designers/shader-designer.md)
- [Węzły projektanta modułu cieniującego](../designers/shader-designer-nodes.md)
