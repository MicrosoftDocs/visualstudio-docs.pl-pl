---
title: 'Instrukcje: Tworzenie cieniowania koloru podstawowego'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f15bba37f5a03da934fae9ba4689da7775cfdb92
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844874"
---
# <a name="how-to-create-a-basic-color-shader"></a>Instrukcje: Tworzenie cieniowania koloru podstawowego

W tym artykule przedstawiono sposób użycia języka programu do cieniowania wykres kierowany (DGSL) i Projektant programu do cieniowania do tworzenie cieniowania koloru. Ten program do cieniowania Ustawia kolor końcowy stałej wartości kolorów RGB.

## <a name="create-a-flat-color-shader"></a>Tworzenie cieniowania koloru

Możesz zaimplementować cieniowania koloru, zapisując wartość koloru stałej kolor RGB kolor końcowych danych wyjściowych.

Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

1. Tworzenie modułu cieniującego DGSL chcesz pracować. Aby uzyskać informacje dotyczące sposobu dodawania modułu cieniującego DGSL do projektu, zobacz sekcję pierwsze kroki w [Shader Designer](../designers/shader-designer.md).

2. Usuń **koloru punktu** węzła. Użyj **wybierz** narzędzie do wybierania **koloru punktu** węzła, a następnie na pasku menu wybierz **Edytuj** > **Usuń**.

3. Dodaj **stała koloru** węzła do wykresu. W **przybornika**w obszarze **stałe**, wybierz opcję **stała koloru** i przenieś go do powierzchni projektowej.

4. Określ wartość koloru **stała koloru** węzła. Użyj **wybierz** narzędzie do wybierania **stała koloru** węzła, a następnie w **właściwości** okna w **dane wyjściowe** właściwości, określ wartość koloru. Na pomarańczowy należy określić wartość (1.0, 0,5, 0.2, 1.0).

5. Stała koloru nawiązać połączenie ostateczny kolor. Pod kątem tworzenia połączeń, należy przenieść **RGB** terminali z **stała koloru** węzeł **RGB** terminali z **ostateczny kolor** węzła, i następnie przenieś **alfa** terminali z **stała koloru** węzeł, aby **alfa** terminali z **ostateczny kolor** węzła. Te połączenia Ustaw kolor końcowy stała koloru zdefiniowane w poprzednim kroku.

Poniższej ilustracji ukończone programu do cieniowania programu graph i wersję zapoznawczą programu do cieniowania stosowane do modułu.

> [!NOTE]
> Na ilustracji koloru pomarańczowego określono lepiej wykazać efekt programu do cieniowania.

![Wykres modułu cieniującego i jego wynik na 3&#45;modelu D](../designers/media/digit-flat-color-effect.png)

Niektórych kształtów udostępniać lepsze wersje zapoznawcze niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat programów do cieniowania w projektancie programu do cieniowania w wersji zapoznawczej, zobacz [Shader Designer](../designers/shader-designer.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: Eksport cieniowania](../designers/how-to-export-a-shader.md)
- [Projektant cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)