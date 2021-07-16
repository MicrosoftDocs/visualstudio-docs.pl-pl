---
title: Warianty filtru tekstur punkt/dwuliniowy/trójliniowy/anisotropowy
description: Jeśli koszt wydajności punktu, dwuliniowego, trójliniowego lub anizotropowego wariantu filtrowania tekstury jest znaczący, możesz rozważyć, czy jego użycie jest opłacalne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d89db195b94bcf31d2ce2c7482c5b7315a979e9
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232651"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Warianty punktowego, dwuliniowego, trójliniowego i anizotropowego filtrowania tekstur
Zastępuje tryb filtrowania na odpowiednich próbkach tekstury.

## <a name="interpretation"></a>Interpretacja
 Różne metody próbkowania tekstur mają różne koszty wydajności i jakość obrazu. W celu zwiększenia kosztów i jakości wizualizacji tryby filtrowania są:

1. Filtrowanie punktów (najdroższa, najgorszą jakość wizualizacji)

2. Filtrowanie dwuliniowe

3. Filtrowanie trójliniowe

4. Filtrowanie anizotropowe (najdroższa, najlepsza jakość wizualizacji)

   Jeśli koszt wydajności każdego wariantu jest znaczący lub zwiększa się wraz z bardziej intensywnymi trybami filtrowania, można rozważyć jego koszt w stosunku do jego zwiększonej jakości obrazu. Na podstawie oceny możesz zaakceptować dodatkowe koszty wydajności, aby zwiększyć jakość wizualizacji, lub zaakceptować obniżenie jakości wizualizacji w celu osiągnięcia większej szybkości klatek lub odzyskania wydajności, która może być inna.

   Jeśli uważasz, że koszt wydajności jest niewielki lub stały niezależnie od trybu filtrowania — na przykład gdy docelowy procesor GPU ma dużą przepływność cieniowania i przepustowość pamięci — rozważ użycie filtrowania anizotropowego w celu uzyskania najlepszej jakości obrazu w aplikacji.

## <a name="remarks"></a>Uwagi
 Te warianty przesłaniają stany sampler w wywołaniach, do których tryb filtru próbkatora dostarczonego przez `ID3D11DeviceContext::PSSetSamplers` aplikację jest jednym z tych:

- `D3D11_FILTER_MIN_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`

- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`

- `D3D11_FILTER_ANISOTROPIC`

  W  wariancie filtrowania tekstur punktów tryb filtru dostarczany przez aplikację został zastąpiony . W wariancie filtrowania tekstury dwuliniowej jest zastępowany przez ; a w wariancie Filtrowanie tekstury trójliniowej jest zastępowany przez `D3D11_FILTER_MIN_MAG_MIP_POINT`  `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  `D3D11_FILTER_MIN_MAG_MIP_LINEAR` .

  W **wariancie filtrowania** tekstury anizotropowej tryb filtru dostarczany przez aplikację jest zastępowany przez wartość , a wartość maksymalna anizotropii jest ustawiona na `D3D11_FILTER_ANISOTROPIC` 16.

## <a name="restrictions-and-limitations"></a>Ograniczenia
 W direct3D poziom funkcji 9.1 określa maksymalną anizotropię 2x. Ponieważ wariant filtrowania tekstury **anizotropowej** próbuje używać wyłącznie 16-x anizotropii, odtwarzanie kończy się niepowodzeniem, gdy analiza klatek jest uruchamiana na urządzeniu na poziomie funkcji 9.1. Urządzenia przenośne, których dotyczy to ograniczenie, obejmują tablety Surface RT i Surface 2 Windows ARM. Może to również mieć wpływ na starsze procesory GPU, które mogą nadal być używane na niektórych komputerach, ale są one powszechnie uznawane za przestarzałe i coraz częściej występują.

## <a name="example-1"></a>Przykład 1
 Wariant **filtrowania tekstur punktów** można odtworzyć przy użyciu kodu podobnego do tego:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-2"></a>Przykład 2
 Wariant **filtrowania tekstury dwuliniowej** można odtworzyć przy użyciu kodu podobnego do tego:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-3"></a>Przykład 3
 Wariant **filtrowania tekstury** trójliniowej można odtworzyć przy użyciu kodu podobnego do tego:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-4"></a>Przykład 4
 Wariant **filtrowania tekstury anizotropowej** można odtworzyć przy użyciu kodu podobnego do tego:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;
sampler_description.MaxAnisotropy = 16;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```
