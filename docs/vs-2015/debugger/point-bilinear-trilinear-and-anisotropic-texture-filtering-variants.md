---
title: Warianty do filtrowania, Trójliniowego i anizotropowego tekstury Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c53f3b0633ec8938de210cb518d9fae1937eb2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185407"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Warianty punktowego, dwuliniowego, trójliniowego i anizotropowego filtrowania tekstur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="example"></a>Przykład  
 Wartość zmiennej **filtrowania tekstury punktów** można odtworzyć przy użyciu kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Przykład  
 Wariant **filtrowania tekstury liniowej** można odtworzyć przy użyciu kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Przykład  
 Wariant **filtrowania tekstury trójliniowego** można odtworzyć przy użyciu kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Przykład  
 Wariant **filtrowania tekstury anizotropowego** można odtworzyć przy użyciu kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```
