---
title: Wariant rozmiaru okienka ekranu 1 x 1 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5b2c96b11c2075ce88b43cdebc34b905141c973
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690425"
---
# <a name="1x1-viewport-size-variant"></a>Wariant rozmiaru 1x1 okienka ekranu
Maksymalne wymiary okienka ekranu na wszystkie elementy docelowe renderowania na 1 x 1 pikseli.

## <a name="interpretation"></a>Interpretacja
 Mniejsze okienka ekranu zmniejsza liczbę pikseli, które wymagają cień. Ale mniejsze okienka ekranu nie zmniejszyć liczbę wierzchołki, które wymagają procesu. Ustawienie wymiary okienka ekranu na 1 x 1 piksel skutecznie eliminuje cieniowania pikseli, z poziomu aplikacji.

 Jeśli ten wariant wykazuje duże są bardziej wydajne, może to wskazywać, że aplikacja zużywa zbyt dużo szybkość wypełniania. Ponadto rozdzielczość może być zbyt duża dla platformy docelowej lub aplikacji może poświęcać dużo czasu na cieniowania pikseli, które później zostaną zastąpione, znany również jako *overdraw*. Mniejsze buforu ramki lub zmniejszyć ilość overdraw poprawi wydajność Twojej aplikacji.

## <a name="remarks"></a>Uwagi
 Wymiary okienka ekranu są resetowane do pikseli 1 x 1 po każdym wywołaniu `ID3D11DeviceContext::OMSetRenderTargets` lub `ID3D11DeviceContext::RSSetViewports`.

## <a name="example"></a>Przykład
 Ten wariant można odtworzyć z następującym kodem:

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
