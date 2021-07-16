---
title: Wariant rozmiaru 1x1 | Microsoft Docs
description: Zastosuj wariant rozmiaruportu ekranu 1x1, aby zmniejszyć wymiaryportu ekranu na wszystkich docelowych renderach do 1x1 pikseli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb8d00d68a61fd2e97740ee46f92433ea34abb65
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232846"
---
# <a name="1x1-viewport-size-variant"></a>Wariant rozmiaru 1x1 okienka ekranu
Zmniejsza wymiary ekranu na wszystkich docelowych renderach do 1x1 pikseli.

## <a name="interpretation"></a>Interpretacja
 Mniejszy ekran zmniejsza liczbę pikseli, które należy zacieniować. Jednak mniejsza ilość wyświetleń nie zmniejsza liczby wierzchołków, które trzeba przetworzyć. Ustawienie wymiarów w widoku na 1x1 pikseli skutecznie eliminuje cieniowanie pikseli z aplikacji.

 Jeśli ten wariant pokazuje duży wzrost wydajności, może to wskazywać, że aplikacja zużywa zbyt dużo wypełnienia. Ponadto rozdzielczość może być zbyt wysoka dla platformy docelowej lub aplikacja może poświęcać znaczną część czasu na cieniowanie pikseli, które są później zastępowane, co jest również wiadomo jako *overdraw*. Mniejszy bufor ramowy lub zmniejszenie ilości przepełnienia poprawi wydajność aplikacji.

## <a name="remarks"></a>Uwagi
 Wymiary w widoku są resetowane do 1x1 pikseli po każdym wywołaniu do `ID3D11DeviceContext::OMSetRenderTargets` lub `ID3D11DeviceContext::RSSetViewports` .

## <a name="example"></a>Przykład
 Ten wariant można odtworzyć za pomocą następującego kodu:

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
