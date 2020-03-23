---
title: 'Porady: tworzenie cieniowania koloru podstawowego'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 162632f0043d23fb111a9e455c1100f9506924a8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589516"
---
# <a name="how-to-create-a-basic-color-shader"></a>Instrukcje: tworzenie cieniowania koloru podstawowego

W tym artykule pokazano, jak utworzyć moduł cieniujący za pomocą projektanta modułu cieniującego i języka cieniowania wykresu kierowanego (DGSL). Ten moduł cieniujący ustawia kolor końcowy na stałą wartość koloru RGB.

## <a name="create-a-flat-color-shader"></a>Tworzenie kolorów płaskich

Moduł cieniujący kolor płaski można zaimplementować, zapisując wartość koloru stałej RGB do końcowego koloru wyjściowego.

Przed rozpoczęciem upewnij się, że są wyświetlane okno **Właściwości** i **Przybornik.**

1. Utwórz moduł cieniujący DGSL do pracy. Aby uzyskać informacje dotyczące dodawania modułu cieniującego DGSL do projektu, zobacz sekcję Wprowadzenie w [Projektancie modułu cieniującego](../designers/shader-designer.md).

2. Usuń węzeł **Kolor punktu.** Użyj narzędzia **Zaznacz,** aby **zaznaczyć** węzeł Kolor punktu, a następnie na pasku menu wybierz pozycję **Edytuj** > **usuń**.

3. Dodaj węzeł **Stałej kolorów** do wykresu. W **przyborniku**w obszarze **Stałe**wybierz pozycję **Stała koloru** i przenieś ją na powierzchnię projektową.

4. Określ wartość koloru dla **węzła Stała koloru.** Użyj narzędzia **Zaznacz,** aby wybrać węzeł **Stała koloru,** a następnie w oknie **Właściwości** we właściwości **Output** określ wartość koloru. W przypadku pomarańczy określ wartość (1,0, 0,5, 0,2, 1,0).

5. Połącz stałą kolorów z kolorem końcowym. Aby utworzyć połączenia, przenieś terminal **RGB** **węzła Stała barwna** do terminalu **RGB** **węzła Kolor końcowy,** a następnie przenieś terminal **Alfa** **węzła Stała kolorów** do terminalu **Alfa** **węzła Kolor.** Połączenia te ustawiają kolor końcowy na stałą kolorów zdefiniowaną w poprzednim kroku.

Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i podgląd modułu cieniującego zastosowanego do modułu.

> [!NOTE]
> Na ilustracji określono kolor pomarańczowy, aby lepiej zademonstrować efekt modułu cieniującego.

![Wykres modułu cieniującego i jego wynik w modelu 3&#45;D](../designers/media/digit-flat-color-effect.png)

Niektóre kształty mogą zapewniać lepsze podglądy niektórych modułów cieniowania. Aby uzyskać więcej informacji na temat wyświetlania podglądu modułów cieniucych w Projektancie modułów cieniucych, zobacz [Projektant modułu cieniującego](../designers/shader-designer.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: eksportowanie cieniowania](../designers/how-to-export-a-shader.md)
- [Projektant modułu cieniującego](../designers/shader-designer.md)
- [Węzły projektanta modułu cieniującego](../designers/shader-designer-nodes.md)
