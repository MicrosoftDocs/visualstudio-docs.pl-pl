---
title: 'Instrukcje: Model terenu 3D'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41974aee19cf1e4919028d5ef0f0e9b53c6b369e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844460"
---
# <a name="how-to-model-3d-terrain"></a>Instrukcje: Modelowanie terenu 3D

W tym artykule przedstawiono sposób używania edytora modelu, aby utworzyć model terenu 3D.

## <a name="create-a-3d-terrain-model"></a>Tworzenie modelu terenu 3D

Możesz utworzyć terenu 3D podpodział płaszczyzny zapewnienie dodatkowych twarzy, a następnie manipulowanie ich wierzchołki, aby tworzyć interesujące funkcje terenu.

Gdy skończysz, model powinien wyglądać następująco:

![3&#45;sceny D, pokazujący model terenu](../designers/media/digit-terrain-model.png)

Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

1. Utwórz model 3D, z którą chcesz pracować. Aby uzyskać informacje dotyczące sposobu dodawania modelu do swojego projektu, zobacz sekcję pierwsze kroki w [edytora modelu](../designers/model-editor.md).

2. Dodaj płaszczyznę do sceny. W **przybornika**w obszarze **kształty**, wybierz opcję **płaszczyzny** i przenieś go do powierzchni projektowej.

    > [!TIP]
    > Aby ułatwić obiektu płaszczyzny chcesz pracować, można ramki go na powierzchnię. W **wybierz** tryb, wybierz obiekt płaszczyzny, a następnie na pasku narzędzi edytora modelu, wybierz **obiekt w ramce** przycisku.

3. Wprowadź trybu wyboru pierwszego planu. Na pasku narzędzi edytora modelu wybierz **wybierz krój**.

4. Należy podzielić płaszczyzny. W przypadku trybu wyboru pierwszego planu wybierz płaszczyzny raz go uaktywnić dla zaznaczenia, a następnie wybierz ją ponownie, aby wybrać jej tylko twarzy. Na pasku narzędzi edytora modelu wybierz **Podziel pierwszy plan**. Spowoduje to dodanie nowe wierzchołki płaszczyzny i podziel go na partycje równej wielkości.

5. Utwórz więcej segmentami. Przy wciąż zaznaczonym nowe powierzchnie, wybierz polecenie **Podziel pierwszy plan** dwa razy. Spowoduje to utworzenie w sumie 64 twarzy. Tworząc więcej segmentami, można nadać terenu jeszcze więcej szczegółów.

6. Przejść do trybu wyboru punktu. Na pasku narzędzi edytora modelu wybierz **wybierz punkt**.

7. Zmodyfikuj punkt, aby utworzyć funkcję terenu. W trybie wyboru punktu, należy wybrać jeden z punktów, a następnie na pasku narzędzi edytora modelu wybierz **Translate** narzędzia. Pole, który reprezentuje punkt jest wyświetlany na powierzchni projektowej. Aby przenieść pole i tym samym zmodyfikować wysokość punktu, użyj zieloną strzałkę. Powtórz ten krok dla różnych punktów w celu utworzenia interesujące funkcje terenu.

    > [!TIP]
    > Możesz wybrać kilka punktów jednocześnie z ich w jednolity sposób.

Model terenu jest kompletny. Poniżej przedstawiono końcowego modelu ponownie przy użyciu cieniowanie Phong zastosowane:

![3&#45;sceny D, pokazujący model terenu](../designers/media/digit-terrain-model.png)

Ten model terenu można użyć, aby zademonstrować efekt modułu cieniującego gradientu, który jest opisany w [jak: Tworzenie cieniowania gradientu geometrycznego](../designers/how-to-create-a-geometry-based-gradient-shader.md).

## <a name="see-also"></a>Zobacz także

- [Edytor modelu](../designers/model-editor.md)