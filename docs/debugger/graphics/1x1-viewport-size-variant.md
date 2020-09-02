---
title: 1x1 — wariant rozmiaru okienka ekranu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5b2c96b11c2075ce88b43cdebc34b905141c973
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62848738"
---
# <a name="1x1-viewport-size-variant"></a>Wariant rozmiaru 1x1 okienka ekranu
Zmniejsza wymiary okienka ekranu dla wszystkich obiektów docelowych renderowania do 1x1 pikseli.

## <a name="interpretation"></a>Interpretacja
 Mniejszy okienko ekranu zmniejsza liczbę pikseli, które trzeba odcieniować. Jednak mniejszym okienkiem ekranu nie jest zmniejszenie liczby wierzchołków, które trzeba przetworzyć. Ustawienie wymiarów okienka ekranu na 1x1 pikseli skutecznie eliminuje cieniowanie pikseli z aplikacji.

 Jeśli ten wariant pokazuje duży wzrost wydajności, może to wskazywać, że aplikacja zużywa zbyt dużą szybkość wypełniania. Ponadto rozwiązanie może być zbyt wysokie dla platformy docelowej lub aplikacja może spędzać *znaczące,* nadmiarowe piksele cieniowania, które są później zastępowane. Mniejszy bufor ramki lub zmniejszenie ilości narysowania poprawi wydajność aplikacji.

## <a name="remarks"></a>Uwagi
 Wymiary okienka ekranu są resetowane do 1x1 pikseli po każdym wywołaniu `ID3D11DeviceContext::OMSetRenderTargets` lub `ID3D11DeviceContext::RSSetViewports` .

## <a name="example"></a>Przykład
 Ten wariant można odtworzyć przy użyciu następującego kodu:

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
