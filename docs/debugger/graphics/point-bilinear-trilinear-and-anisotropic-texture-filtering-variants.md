---
title: Warianty dla filtrów tekstury punkt/liniowy/trójliniowego/anizotropowego
description: Jeśli koszt wydajności punktu, wieloliniowego, trójliniowego lub wariantu filtrowanie tekstury anizotropowego jest istotny, można rozważyć, czy jego użycie jest kosztem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c38869b4c8daa4cb4433f9f6a64afcc7398c9a9c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996087"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Warianty punktowego, dwuliniowego, trójliniowego i anizotropowego filtrowania tekstur
Zastępuje tryb filtrowania odpowiednich próbników tekstury.

## <a name="interpretation"></a>Interpretacja
 Różne metody próbkowania tekstury mają różne koszty wydajności i jakość obrazu. W celu zwiększenia kosztów — i zwiększenia jakości wizualnej — tryby filtru są następujące:

1. Filtrowanie punktów (co najmniej kosztowna, najgorsza jakość wizualna)

2. Filtrowanie liniowe

3. Filtrowanie trójliniowego

4. Filtrowanie anizotropowego (najbardziej kosztowne, Najlepsza jakość wizualna)

   Jeśli koszt wydajności każdego wariantu jest znaczący lub zwiększa się dzięki bardziej intensywnym trybom filtrowania, możesz poważyć swój koszt w porównaniu z zwiększoną jakością obrazu. Na podstawie oceny można zaakceptować dodatkowe koszty związane z wydajnością w celu zwiększenia jakości wizualnej lub zaakceptowania zmniejszonej jakości wizualnej w celu osiągnięcia wyższej szybkości klatek lub odzyskiwania wydajności, z której można korzystać w inny sposób.

   Jeśli okaże się, że koszt wydajności jest nieznaczny lub niestabilny niezależnie od trybu filtrowania — na przykład gdy docelowy procesor GPU ma liczebność przepływności i przepustowości pamięci — Rozważ użycie filtrowania anizotropowego w celu uzyskania najlepszej jakości obrazu w aplikacji.

## <a name="remarks"></a>Uwagi
 Te warianty przesłaniają Stany próbnika na wywołaniach, `ID3D11DeviceContext::PSSetSamplers` w których tryb filtrowania dostarczony przez aplikację jest jednym z następujących:

- `D3D11_FILTER_MIN_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`

- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`

- `D3D11_FILTER_ANISOTROPIC`

  W przypadku wariantu **filtrowania tekstury** tryb filtru podany w aplikacji jest zastępowany `D3D11_FILTER_MIN_MAG_MIP_POINT` ; w elemencie Variant **tekstury tekstura liniowa** jest zastępowana wartością, `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT` a w elemencie Variant **trójliniowego Texture Filtering** jest zastępowany `D3D11_FILTER_MIN_MAG_MIP_LINEAR` .

  W elemencie Variant **anizotropowego Texture** filters tryb filtru udostępniony przez aplikację jest zastępowany `D3D11_FILTER_ANISOTROPIC` , a maksymalna anisotropy jest ustawiona na 16.

## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia
 W programie Direct3D poziom funkcji 9,1 określa maksymalną anisotropy. Ponieważ wariant **filtru tekstury anizotropowego** próbuje użyć wyłącznie 16x anisotropy, odtwarzanie kończy się niepowodzeniem, gdy analiza klatek jest uruchamiana na urządzeniu 9,1 na poziomie funkcji. Współczesne urządzenia, na które ma wpływ ten limit, obejmują tablety czołowe i Surface 2 systemu Windows. Mogą być również narażone starsze procesory GPU, które nadal mogą znajdować się na niektórych komputerach, ale są one powszechnie uznawane za przestarzałe i coraz bardziej niespotykane.

## <a name="example-1"></a>Przykład 1
 Wartość zmiennej **filtrowania tekstury punktów** można odtworzyć przy użyciu kodu w następujący sposób:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-2"></a>Przykład 2
 Wariant **filtrowania tekstury liniowej** można odtworzyć przy użyciu kodu w następujący sposób:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-3"></a>Przykład 3
 Wariant **filtrowania tekstury trójliniowego** można odtworzyć przy użyciu kodu w następujący sposób:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-4"></a>Przykład 4
 Wariant **filtrowania tekstury anizotropowego** można odtworzyć przy użyciu kodu w następujący sposób:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;
sampler_description.MaxAnisotropy = 16;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```
