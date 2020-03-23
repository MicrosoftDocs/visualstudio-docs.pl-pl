---
title: 'Jak: Tworzenie podstawowego modelu 3D'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce16e436172a7d369f2df8342f6b027b574056ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589529"
---
# <a name="how-to-create-a-basic-3d-model"></a>Instrukcje: tworzenie podstawowego modelu 3D

W tym artykule pokazano, jak za pomocą Edytora modeli do tworzenia podstawowego modelu 3D. Następujące działania są objęte:

- Dodawanie obiektów do sceny

- Wybieranie ścian i krawędzi

- Tłumaczenie zaznaczeń

- Korzystanie z narzędzi **Podziel ścianę** i **wyciągnięcie ściany**

- Korzystanie z polecenia **Triangulate**

## <a name="create-a-basic-3d-model"></a>Tworzenie podstawowego modelu 3D
Edytor modeli służy do tworzenia i modyfikowania modeli i scen 3D dla gry lub aplikacji. Poniższe kroki pokazują, jak za pomocą Edytora modeli, aby utworzyć uproszczony model 3D domu. Uproszczony model może służyć jako stand-in dla końcowych zasobów sztuki, które są nadal tworzone, jako siatki do wykrywania kolizji lub jako model o niskiej szczegółowości, który ma być używany, gdy obiekt, który reprezentuje jest zbyt daleko, aby korzystać z bardziej szczegółowego renderowania.

Po zakończeniu model powinien wyglądać następująco:

![Ukończony model uproszczonego domu](../designers/media/gfx_model_demo_house_final.png)

Przed rozpoczęciem upewnij się, że są wyświetlane okna **Właściwości** i **Przybornik.**

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Aby utworzyć uproszczony model 3D domu

1. Utwórz model 3D, z którym ma być do pracy. Aby uzyskać informacje dotyczące dodawania modelu do projektu, zobacz sekcję Wprowadzenie w [Edytorze modeli](../designers/model-editor.md).

2. Dodaj kostkę do sceny. W oknie **Przybornik** w obszarze **Kształty**wybierz pozycję **Sześcian,** a następnie przenieś go na powierzchnię projektową.

3. Przełącz się na wybór twarzy. Na pasku narzędzi Edytor modeli wybierz pozycję **Wybierz ścianę**.

4. Podziel górną część sześcianu. W trybie wyboru twarzy wybierz moduł raz, aby aktywować go do zaznaczenia, a następnie wybierz górną część sześcianu, aby wybrać górną ścianę. Na pasku narzędzi Edytor modeli wybierz pozycję **Podziel ścianę**. Spowoduje to dodanie nowych wierzchołków do górnej części modułu, który dzieli go na cztery partycje o jednakowym rozmiarze.

    ![Górna część sześcianu została podzielona](../designers/media/gfx_model_demo_house_subdiv.png)

5. Wyciągnięcie dwóch sąsiadujących stron sześcianu — na przykład przedniej i prawej strony sześcianu. W trybie wyboru twarzy wybierz moduł raz, aby aktywować go do wyboru, a następnie wybierz jedną stronę modułu. Naciśnij i przytrzymaj klawisz **Ctrl,** wybierz inną stronę modułu, która sąsiaduje najpierw z zaznaczoną stroną, a następnie na pasku narzędzi Edytor modelu wybierz pozycję **Wyciągnięcie ściany**.

    ![Boki sześcianu zostały wytłaczane](../designers/media/gfx_model_demo_house_extrude.png)

6. Wydłużyć jedno z wytężówek. Wybierz jedną z ścian, które zostały właśnie wyciągone, a następnie na pasku narzędzi Edytor modelu wybierz narzędzie **Tłumacz** i przesuń manipulator translacji w tym samym kierunku co wyciągnięcie.

    ![Jedna strona sześcianu została wytłaczana dalej.](../designers/media/gfx_model_demo_house_extend.png)

7. Triangulate modelu. Na pasku narzędzi Edytor modeli wybierz pozycję **Zaawansowane** > **narzędzia** > **triangulacyjne**.

8. Stwórz dach domu. Przełącz się do trybu wyboru krawędzi, wybierając **pozycję Wybierz krawędź** na pasku narzędzi Edytor modelu, a następnie wybierz moduł, aby go uaktywnić. Naciśnij i przytrzymaj klawisz **Ctrl** podczas wybierania krawędzi, które są wyświetlane w tym miejscu:

    ![Krawędzie, które będą tworzyć szczyt dachu](../designers/media/gfx_model_demo_house_edges.png)

    Po wybraniu krawędzi na pasku narzędzi Edytor modelu wybierz narzędzie **Tłumacz,** a następnie przesuń manipulator tłumaczenia w górę, aby utworzyć dach domu.

   Uproszczony model domu jest kompletny. Oto ostatni model ponownie, z płaskim cieniowaniem stosowane:

   ![Ukończony model uproszczonego domu](../designers/media/gfx_model_demo_house_final.png)

   W następnym kroku można zastosować moduł cieniujący do tego modelu 3D. Aby uzyskać więcej informacji, zobacz [Jak: Stosowanie modułu cieniującego do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz też

- [Jak: Model 3D terenu](../designers/how-to-model-3-d-terrain.md)
- [Edytor modelu](../designers/model-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)
