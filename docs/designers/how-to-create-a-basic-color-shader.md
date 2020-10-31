---
title: 'Porady: tworzenie cieniowania koloru podstawowego'
description: Dowiedz się, jak używać projektanta cieniowania i ukierunkowanego języka cieniowania wykresów, aby utworzyć cieniowanie kolorami prostymi, które ustawia kolor końcowy na stałą wartość koloru RGB.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d966a8fdc565eae5254d21dba4ab9dfaa440de94
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134109"
---
# <a name="how-to-create-a-basic-color-shader"></a>Instrukcje: tworzenie cieniowania koloru podstawowego

W tym artykule pokazano, jak używać projektanta programu do cieniowania i języka programu do cieniowania grafów (DGSL) w celu utworzenia cieniowania prostego koloru. Ten program do cieniowania ustawia kolor końcowy na stałą wartość koloru RGB.

## <a name="create-a-flat-color-shader"></a>Tworzenie cieniowania koloru prostego

Można zaimplementować cieniowanie koloru prostego, pisząc wartość koloru stałej koloru RGB do końcowego koloru wyjściowego.

Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

1. Utwórz program do cieniowania DGSL. Aby dowiedzieć się, jak dodać cieniowanie DGSL do projektu, zobacz sekcję Wprowadzenie w [projektancie cieniowania](../designers/shader-designer.md).

2. Usuń węzeł **koloru punktu** . Za pomocą narzędzia **Wybierz** wybierz węzeł **Kolor punktu** , a następnie na pasku menu wybierz polecenie **Edytuj**  >  **Usuń** .

3. Dodaj węzeł **stałej koloru** do grafu. W **przyborniku** , w obszarze **stałe** , wybierz pozycję **kolor stała** i przenieś ją do powierzchni projektowej.

4. Określ wartość koloru dla węzła **stałego koloru** . Użyj narzędzia **Wybierz** , aby wybrać węzeł **stałej koloru** , a następnie w oknie **Właściwości** , we właściwości **Output** , określić wartość koloru. Dla elementu pomarańczowego Określ wartość (1,0, 0,5, 0,2, 1,0).

5. Połącz stałą koloru z końcowym kolorem. Aby utworzyć połączenia, należy przenieść Terminal **RGB** węzła **stała koloru** do terminalu **RGB** **końcowego węzła koloru** , a następnie przenieść Terminal **alfa** węzła **stała kolor** do terminalu **alfa** **końcowego węzła koloru** . Te połączenia ustawiają końcowy kolor na stałą koloru zdefiniowaną w poprzednim kroku.

Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i Podgląd cieniowania zastosowany do modułu.

> [!NOTE]
> Na ilustracji określono pomarańczowy kolor, aby lepiej zademonstrować efekt cieniowania.

![Cieniowanie grafu i jego wynik na modelu 3&#45;D](../designers/media/digit-flat-color-effect.png)

Niektóre kształty mogą zapewniać lepszy Podgląd niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat podglądu programów do cieniowania w projektancie cieniowania, zobacz [Projektant cieniowania](../designers/shader-designer.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: eksportowanie cieniowania](../designers/how-to-export-a-shader.md)
- [Projektant programu do cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)
