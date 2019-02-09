---
title: 'Instrukcje: Tworzenie podstawowego modelu 3D'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45944afe3c5ebd1baa307f6063b021c09fd6bfa6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970273"
---
# <a name="how-to-create-a-basic-3d-model"></a>Instrukcje: Tworzenie podstawowego modelu 3D

W tym artykule przedstawiono sposób używania edytora modelu do tworzenia podstawowego modelu 3D. Omówione są następujące działania:

-   Dodawanie obiektów do sceny

-   Wybieranie powierzchni i krawędzi

-   Opcje przekształcania

-   Za pomocą **Podziel pierwszy plan** i **wyciągnij** narzędzia

-   Za pomocą **triangulacja** polecenia

## <a name="create-a-basic-3d-model"></a>Tworzenie podstawowego modelu 3D
 Edytor modelu do tworzenia i modyfikowania modeli 3D i sceny gry lub aplikacji. Poniższe kroki pokazują jak utworzyć uproszczony model 3D w domu za pomocą edytora modelu. Uproszczony model może służyć jako elementu zastępczego dla końcowego artystycznych, które są nadal tworzone, jako siatkę wykrywanie kolizji lub niska Szczegóły modelu ma być używany, gdy obiekt, który reprezentuje jest zbyt daleko do korzystania z renderowania bardziej szczegółowe.

 Gdy skończysz, model powinien wyglądać następująco:

 ![Ukończone modelu DOM uproszczony](../designers/media/gfx_model_demo_house_final.png)

 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Aby utworzyć uproszczony model 3D w domu

1. Utwórz model 3D, z którą chcesz pracować. Aby uzyskać informacje dotyczące sposobu dodawania modelu do swojego projektu, zobacz sekcję pierwsze kroki w [edytora modelu](../designers/model-editor.md).

2. Dodaj moduł do sceny. W **przybornika** okna, w obszarze **kształty**, wybierz opcję **modułu** i przenieś go do powierzchni projektowej.

3. Przełącz się do wyboru twarzy. Na pasku narzędzi edytora modelu wybierz **wybierz krój**.

4. Należy podzielić górnej części modułu. W przypadku trybu wyboru pierwszego planu wybierz moduł raz go uaktywnić dla zaznaczenia, a następnie wybierz górnej części modułu, aby zaznacz powierzchnię, najważniejsze. Na pasku narzędzi edytora modelu wybierz **Podziel pierwszy plan**. Spowoduje to dodanie nowe wierzchołki na początku modułu, który podzielić ją na cztery partycje równej wielkości.

    ![Górnej części modułu zostały podzielone](../designers/media/gfx_model_demo_house_subdiv.png)

5. Wyciągnięcie dwóch sąsiednich boków modułu — na przykład frontonu i prawej stronie modułu. W trybu wyboru pierwszego planu wybierz moduł raz go uaktywnić dla zaznaczenia, a następnie wybierz polecenie po jednej stronie modułu. Naciśnij i przytrzymaj klawisz **Ctrl** klucza, wybierz inny boku modułu, która jest przyległa do strony, należy najpierw wybrać, a następnie na pasku narzędzi edytora modelu, wybierz **wyciągnij**.

    ![Boków modułu została wyrzucane.](../designers/media/gfx_model_demo_house_extrude.png)

6. Jedną z extrusions rozszerzyć. Wybierz jedną z twarzy, które właśnie, usunąć, a następnie na pasku narzędzi edytora modelu wybierz **Translate** narzędzia i Przenieś manipulator tłumaczenia w tym samym kierunku co wytłaczanie metali.

    ![Dodatkowo ma zostały wyrzucane po jednej stronie modułu.](../designers/media/gfx_model_demo_house_extend.png)

7. Przeprowadzić triangulację modelu. Na pasku narzędzi edytora modelu wybierz **zaawansowane** > **narzędzia** > **triangulacja**.

8. Utwórz dachu domu. Przełącz do trybu wyboru krawędzi, wybierając **krawędzi wybierz pozycję** na pasku narzędzi edytora modelu, a następnie wybierz moduł, aby ją uaktywnić. Naciśnij i przytrzymaj klawisz **Ctrl** klucza podczas zaznaczania krawędzi, które przedstawiono poniżej:

    ![Krawędzie, tworzące Szczyt dachu](../designers/media/gfx_model_demo_house_edges.png)

    Po wybraniu krawędzie, na pasku narzędzi edytora modelu, wybierz **Translate** narzędzia, a następnie przenieść manipulator tłumaczenia w górę, aby utworzyć dachu domu.

   Model DOM uproszczone zostało ukończone. Oto ponownie końcowego modelu z płaskim cieniowaniem stosowane:

   ![Ukończone modelu DOM uproszczony](../designers/media/gfx_model_demo_house_final.png)

   Kolejnym krokiem może stosowanie cieniowania do modelu 3D. Aby uzyskać informacje, zobacz [jak: Stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Model terenu 3D](../designers/how-to-model-3-d-terrain.md)
- [Edytor modelu](../designers/model-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)
