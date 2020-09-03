---
title: 'Instrukcje: Tworzenie podstawowego modelu 3-D | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b4db5b54f39a0be6de184b609e672b1f0173890
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664599"
---
# <a name="how-to-create-a-basic-3-d-model"></a>Porady: tworzenie podstawowego modelu 3-D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób użycia Edytora modelu do utworzenia podstawowego modelu 3-D.

 W tym dokumencie przedstawiono następujące działania:

- Dodawanie obiektów do sceny

- Wybieranie twarzy i krawędzi

- Tłumaczenie wybranych opcji

- Korzystanie z **narzędzi do tworzenia i** **wyciągnięcie kroju**

- Korzystanie z polecenia **triangulacja**

## <a name="creating-a-basic-3-d-model"></a>Tworzenie podstawowego modelu 3-D
 Korzystając z edytora modelu, można tworzyć i modyfikować modele trójwymiarowe oraz sceny dla gier lub aplikacji. Poniższe kroki pokazują, jak za pomocą edytora modelu utworzyć uproszczony model 3-D domu. Model uproszczony może służyć jako autonomiczna dla końcowych zasobów grafiki, które są nadal tworzone, jako siatka do wykrywania kolizji lub jako model niskiego szczegółowości, który ma być używany, gdy obiekt, który reprezentuje, jest zbyt daleko, aby można było skorzystać z bardziej szczegółowego renderowania.

 Po zakończeniu model powinien wyglądać następująco:

 ![Ukończony model uproszczonego](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")

 Przed rozpoczęciem upewnij się, że okno **Właściwości** i **Przybornik** są wyświetlane.

#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>Aby utworzyć uproszczony model 3-D dla domu

1. Utwórz model trójwymiarowy, z którym chcesz współpracować. Aby uzyskać informacje o sposobach dodawania modelu do projektu, zobacz sekcję Wprowadzenie w [Edytorze modelu](../designers/model-editor.md).

2. Dodaj moduł do sceny. W oknie **Przybornik** w obszarze **kształty**wybierz pozycję **moduł** , a następnie przenieś ją na powierzchnię projektu.

3. Przełącz się na wybór obszaru. Na pasku narzędzi Edytor modelu wybierz **pozycję Wybierz opcję**.

4. Podziel górną część modułu. W trybie zaznaczania ze stroną wybierz moduł jeden raz, aby aktywować go do wyboru, a następnie wybierz górną część modułu, aby zaznaczyć górną miarę. Na pasku narzędzi Edytor **modelu wybierz opcję**Podziel na siebie. Spowoduje to dodanie nowych wierzchołków na górze modułu, który dzieli go na cztery partycje o równym rozmiarze.

    ![Górna część modułu została podzielona](../designers/media/gfx-model-demo-house-subdiv.png "gfx_model_demo_house_subdiv")

5. Wyciągnięcie dwóch sąsiadujących stron modułu — na przykład z przodu i po prawej stronie modułu. W trybie wyboru kroju wybierz moduł jeden raz, aby aktywować go do wyboru, a następnie wybierz jedną stronę modułu. Naciśnij i przytrzymaj klawisz sterowania, wybierz inną stronę modułu, która znajduje się obok zaznaczonej pierwszej strony, a następnie na pasku narzędzi Edytor modelu wybierz polecenie **wyciągnięcie kroju**.

    ![Boki modułu zostały wywytłaczane](../designers/media/gfx-model-demo-house-extrude.png "gfx_model_demo_house_extrude")

6. Poszerzenie jednego z wytłoczeniów. Wybierz jedną z wysuniętych twarzy, a następnie na pasku narzędzi Edytor modelu wybierz narzędzie **translacji** i Przenieś Manipulator tłumaczenia w tym samym kierunku co wytłoczenie.

    ![Jedna strona modułu została przeprojektowana w dalszej części.](../designers/media/gfx-model-demo-house-extend.png "gfx_model_demo_house_extend")

7. Triangulacja modelu. Na pasku narzędzi Edytor modelu wybierz pozycję **Zaawansowane**, **Narzędzia**, **triangulacja**.

8. Utwórz dach domu. Przejdź do trybu wyboru krawędzi, wybierając **pozycję Wybierz krawędź** na pasku narzędzi Edytor modelu, a następnie wybierz moduł, aby go uaktywnić. Naciśnij i przytrzymaj klawisz CTRL podczas zaznaczania krawędzi, które są wyświetlane w tym miejscu:

    ![Krawędzie, które będą stanowić szczyt dachu](../designers/media/gfx-model-demo-house-edges.png "gfx_model_demo_house_edges")

    Po wybraniu krawędzi na pasku narzędzi Edytor modelu wybierz narzędzie **translacja** , a następnie przenieś tłumaczenie Manipulator do góry, aby utworzyć dach domu.

   Model uproszczonej konstrukcji został ukończony. Poniżej znajduje się ostateczny model z zastosowanym płaskim cieniowaniem:

   ![Ukończony model uproszczonego](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")

   W następnym kroku można zastosować cieniowanie do tego modelu 3-D. Aby uzyskać więcej informacji, zobacz [jak: Stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz też
 [Jak modelować](../designers/how-to-model-3-d-terrain.md) [projektanta cieniowania](../designers/shader-designer.md) [Edytora modelu](../designers/model-editor.md) 3W
