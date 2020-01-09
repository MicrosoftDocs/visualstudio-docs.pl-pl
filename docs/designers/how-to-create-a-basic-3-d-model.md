---
title: 'Instrukcje: Tworzenie podstawowego modelu 3W'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce16e436172a7d369f2df8342f6b027b574056ab
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589529"
---
# <a name="how-to-create-a-basic-3d-model"></a>Instrukcje: Tworzenie podstawowego modelu 3W

W tym artykule pokazano, jak utworzyć podstawowy model 3W przy użyciu edytora modelu. Omówione są następujące działania:

- Dodawanie obiektów do sceny

- Wybieranie twarzy i krawędzi

- Tłumaczenie wybranych opcji

- Korzystanie z **narzędzi do tworzenia i** **wyciągnięcie kroju**

- Korzystanie z polecenia **triangulacja**

## <a name="create-a-basic-3d-model"></a>Tworzenie podstawowego modelu 3D
Możesz użyć edytora modelu, aby utworzyć i zmodyfikować modele 3D i sceny dla swojej gry lub aplikacji. Poniższe kroki pokazują, jak za pomocą edytora modelu utworzyć uproszczony model 3W dla domu. Model uproszczony może służyć jako autonomiczna dla końcowych zasobów grafiki, które są nadal tworzone, jako siatka do wykrywania kolizji lub jako model niskiego szczegółowości, który ma być używany, gdy obiekt, który reprezentuje, jest zbyt daleko, aby można było skorzystać z bardziej szczegółowego renderowania.

Po zakończeniu model powinien wyglądać następująco:

![Ukończony model uproszczonego](../designers/media/gfx_model_demo_house_final.png)

Przed rozpoczęciem upewnij się, że okno **Właściwości** i **Przybornik** są wyświetlane.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Aby utworzyć uproszczony model 3W dla domu

1. Utwórz model 3W, z którym chcesz korzystać. Aby uzyskać informacje o sposobach dodawania modelu do projektu, zobacz sekcję Wprowadzenie w [Edytorze modelu](../designers/model-editor.md).

2. Dodaj moduł do sceny. W oknie **Przybornik** w obszarze **kształty**wybierz pozycję **moduł** , a następnie przenieś ją na powierzchnię projektu.

3. Przełącz się na wybór obszaru. Na pasku narzędzi Edytor modelu wybierz **pozycję Wybierz opcję**.

4. Podziel górną część modułu. W trybie zaznaczania ze stroną wybierz moduł jeden raz, aby aktywować go do wyboru, a następnie wybierz górną część modułu, aby zaznaczyć górną miarę. Na pasku narzędzi Edytor **modelu wybierz opcję**Podziel na siebie. Spowoduje to dodanie nowych wierzchołków na górze modułu, który dzieli go na cztery partycje o równym rozmiarze.

    ![Górna część modułu została podzielona](../designers/media/gfx_model_demo_house_subdiv.png)

5. Wyciągnięcie dwóch sąsiadujących stron modułu — na przykład z przodu i po prawej stronie modułu. W trybie wyboru kroju wybierz moduł jeden raz, aby aktywować go do wyboru, a następnie wybierz jedną stronę modułu. Naciśnij i przytrzymaj klawisz **Ctrl** , wybierz inną stronę modułu, która znajduje się obok zaznaczonej pierwszej strony, a następnie na pasku narzędzi Edytor modelu wybierz polecenie **wyciągnięcie kroju**.

    ![Boki modułu zostały wywytłaczane](../designers/media/gfx_model_demo_house_extrude.png)

6. Poszerzenie jednego z wytłoczeniów. Wybierz jedną z wysuniętych twarzy, a następnie na pasku narzędzi Edytor modelu wybierz narzędzie **translacji** i Przenieś Manipulator tłumaczenia w tym samym kierunku co wytłoczenie.

    ![Jedna strona modułu została przeprojektowana w dalszej części.](../designers/media/gfx_model_demo_house_extend.png)

7. Triangulacja modelu. Na pasku narzędzi Edytor modelu wybierz kolejno opcje **zaawansowane** > **Narzędzia** > **triangulacja**.

8. Utwórz dach domu. Przejdź do trybu wyboru krawędzi, wybierając **pozycję Wybierz krawędź** na pasku narzędzi Edytor modelu, a następnie wybierz moduł, aby go uaktywnić. Naciśnij i przytrzymaj klawisz **Ctrl** podczas zaznaczania krawędzi, które są wyświetlane w tym miejscu:

    ![Krawędzie, które będą stanowić szczyt dachu](../designers/media/gfx_model_demo_house_edges.png)

    Po wybraniu krawędzi na pasku narzędzi Edytor modelu wybierz narzędzie **translacja** , a następnie przenieś tłumaczenie Manipulator do góry, aby utworzyć dach domu.

   Model uproszczonej konstrukcji został ukończony. Poniżej znajduje się ostateczny model z zastosowanym płaskim cieniowaniem:

   ![Ukończony model uproszczonego](../designers/media/gfx_model_demo_house_final.png)

   W następnym kroku można zastosować cieniowanie do tego modelu 3W. Aby uzyskać więcej informacji, zobacz [How to: Apply a Shader to the 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: modelowanie terenu 3D](../designers/how-to-model-3-d-terrain.md)
- [Edytor modelu](../designers/model-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)
