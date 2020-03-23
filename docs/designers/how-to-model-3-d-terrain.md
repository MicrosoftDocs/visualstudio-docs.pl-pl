---
title: 'Jak: Model 3D Terrain'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a863834790683b229c17ad55b9930a2b382c027b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589425"
---
# <a name="how-to-model-3d-terrain"></a>Jak: Model 3D terenu

W tym artykule pokazano, jak za pomocą Edytora modeli do tworzenia modelu terenu 3D.

## <a name="create-a-3d-terrain-model"></a>Tworzenie modelu terenu 3D

Można utworzyć teren 3D, podzielając płaszczyznę, aby utworzyć dodatkowe ściany, a następnie manipulując ich wierzchołkami, aby utworzyć ciekawe obiekty terenu.

Po zakończeniu model powinien wyglądać następująco:

![3&#45;scena D, która pokazuje model terenu](../designers/media/digit-terrain-model.png)

Przed rozpoczęciem upewnij się, że są wyświetlane okna **Właściwości** i **Przybornik.**

1. Utwórz model 3D, z którym ma być do pracy. Aby uzyskać informacje dotyczące dodawania modelu do projektu, zobacz sekcję Wprowadzenie w [edytorze modelu](../designers/model-editor.md).

2. Dodaj płaszczyznę do sceny. W **przyborniku**w obszarze **Kształty**wybierz pozycję **Płaszczyzna** i przenieś ją na powierzchnię projektową.

    > [!TIP]
    > Aby ułatwić pracę z obiektem płaszczyzny, można go oprawić w powierzchni projektowej. W trybie **wyboru** zaznacz obiekt płaszczyzny, a następnie na pasku narzędzi Edytor modelu wybierz przycisk **Obiekt ramki.**

3. Wprowadź tryb wyboru twarzy. Na pasku narzędzi Edytor modeli wybierz pozycję **Wybierz ścianę**.

4. Podziel płaszczyznę. W trybie wyboru twarzy wybierz płaszczyznę raz, aby aktywować ją do wyboru, a następnie wybierz ją ponownie, aby wybrać jej jedyną ścianę. Na pasku narzędzi Edytor modeli wybierz pozycję **Podziel ścianę**. Spowoduje to dodanie nowych wierzchołków do płaszczyzny, które dzielą go na cztery partycje o jednakowym rozmiarze.

5. Tworzenie większej liczby podpodziałów. Gdy nowe ściany są nadal zaznaczone, wybierz opcję **Podziel twarz** jeszcze dwa razy. Spowoduje to utworzenie łącznie 64 ścian. Tworząc więcej pododdziałów, można nadać terenowi jeszcze więcej szczegółów.

6. Wprowadź tryb wyboru punktu. Na pasku narzędzi Edytor modeli wybierz pozycję **Wybierz punkt**.

7. Zmodyfikuj punkt, aby utworzyć operację terenu. W trybie wyboru punktów wybierz jeden z punktów, a następnie na pasku narzędzi Edytor modelu wybierz narzędzie **Tłumacz.** Pole reprezentujące punkt pojawi się na powierzchni projektowej. Użyj zielonej strzałki, aby przesunąć pole, a tym samym zmodyfikować wysokość punktu. Powtórz ten krok dla różnych punktów, aby utworzyć ciekawe obiekty terenu.

    > [!TIP]
    > Można wybrać kilka punktów jednocześnie, aby zmodyfikować je w jednolity sposób.

Model terenu jest kompletny. Oto ostateczny model ponownie, z Phong cieniowania stosowane:

![3&#45;scena D, która pokazuje model terenu](../designers/media/digit-terrain-model.png)

Za pomocą tego modelu terenu można zademonstrować wpływ modułu cieniującego gradientu opisanego w [temacie Jak: Tworzenie modułu cieniującego gradientu opartego na geometrii](../designers/how-to-create-a-geometry-based-gradient-shader.md).

## <a name="see-also"></a>Zobacz też

- [Edytor modelu](../designers/model-editor.md)
