---
title: 'Instrukcje: Tworzenie podstawowego programu do cieniowania kolorów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90f27e2359954e56a5b3d86bfc31883d4f29c44d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664584"
---
# <a name="how-to-create-a-basic-color-shader"></a>Porady: tworzenie cieniowania koloru podstawowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób korzystania z projektanta programu do cieniowania i języka ukierunkowanego programu Graph (DGSL) w celu utworzenia cieniowania prostego koloru. Ten program do cieniowania ustawia kolor końcowy na stałą wartość koloru RGB.

 W tym dokumencie przedstawiono następujące działania:

- Usuwanie węzłów z grafu

- Dodawanie węzłów do wykresu

- Ustawianie właściwości węzła

- Łączenie węzłów

## <a name="creating-a-flat-color-shader"></a>Tworzenie cieniowania koloru prostego
 Można zaimplementować cieniowanie koloru prostego, pisząc wartość koloru stałej koloru RGB do końcowego koloru wyjściowego.

 Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

#### <a name="to-create-a-flat-color-shader"></a>Aby utworzyć cieniowanie koloru prostego

1. Utwórz program do cieniowania DGSL. Aby dowiedzieć się, jak dodać cieniowanie DGSL do projektu, zobacz sekcję Wprowadzenie w [projektancie cieniowania](../designers/shader-designer.md).

2. Usuń węzeł **koloru punktu** . Za pomocą narzędzia **Wybierz** wybierz węzeł **Kolor punktu** , a następnie na pasku menu wybierz polecenie **Edytuj**, **Usuń**.

3. Dodaj węzeł **stałej koloru** do grafu. W **przyborniku**, w obszarze **stałe**, wybierz pozycję **kolor stała** i przenieś ją do powierzchni projektowej.

4. Określ wartość koloru dla węzła **stałego koloru** . Użyj narzędzia **Wybierz** , aby wybrać węzeł **stałej koloru** , a następnie w oknie **Właściwości** , we właściwości **Output** , określić wartość koloru. Dla elementu pomarańczowego Określ wartość (1,0, 0,5, 0,2, 1,0).

5. Połącz stałą koloru z końcowym kolorem. Aby utworzyć połączenia, należy przenieść Terminal **RGB** węzła **stała koloru** do terminalu **RGB** **końcowego węzła koloru** , a następnie przenieść Terminal **alfa** węzła **stałego koloru** do **alfa** Terminal końcowego węzła **koloru** . Te połączenia ustawiają końcowy kolor na stałą koloru zdefiniowaną w poprzednim kroku.

   Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i Podgląd cieniowania zastosowany do modułu.

> [!NOTE]
> Na ilustracji określono pomarańczowy kolor, aby lepiej zademonstrować efekt cieniowania.

 ![Wykres cieniowania i jego wynik na modelu&#45;3 D](../designers/media/digit-flat-color-effect.png "Cyfra — efekt prostego koloru")

 Niektóre kształty mogą zapewniać lepszy Podgląd niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat podglądu programów do cieniowania w projektancie cieniowania, zobacz [Projektant cieniowania](../designers/shader-designer.md).

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [instrukcje: eksportowanie](../designers/how-to-export-a-shader.md) [](../designers/shader-designer.md) [węzłów projektanta](../designers/shader-designer-nodes.md) cieniowania programu do cieniowania
