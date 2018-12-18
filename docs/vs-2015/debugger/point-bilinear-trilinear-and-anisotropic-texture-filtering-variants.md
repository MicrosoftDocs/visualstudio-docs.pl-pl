---
title: Punkt, warianty punktowego, Trójliniowego i Anizotropowego filtrowania tekstur | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef054b1773b1f0d07e21ec25cb326594a4d3b2d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791243"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Warianty punktowego, dwuliniowego, trójliniowego i anizotropowego filtrowania tekstur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zastępuje tryb filtrowania na próbników odpowiednie tekstury.  
  
## <a name="interpretation"></a>Interpretacja  
 Różne metody pobierania próbek tekstury ma koszty wydajności i jakości obrazu. W celu zwiększenia kosztów — oraz zwiększyć jakość wizualną — są tryby filtrowania:  
  
1. Polecenie Filtrowanie (jakość najniższy, najgorzej visual)  
  
2. Warianty punktowego filtrowania  
  
3. Filtrowanie trójliniowego  
  
4. Anizotropowego filtrowania (jakość najbardziej kosztowne, najlepiej visual)  
  
   Jeśli spadek wydajności przy każdym wariant jest znaczący, zwiększa się wraz z intensywnie korzystających z innych trybów filtrowania można porównać jego kosztów względem jego zwiększona jakość. Oparte na swoją ocenę, można przyjąć koszty dodatkowej wydajności, aby zwiększyć jakość wizualną lub można przyjąć zmniejszyła się jakość wizualną, w celu uzyskania większej szybkości odtwarzania lub odzyskać wydajności używanego w inny sposób.  
  
   Jeśli okaże się, że spadek wydajności jest niewielki lub stały niezależnie od tego trybu filtrowania — na przykład w przypadku, gdy procesora GPU, który zostaną objęci zawiera licznych przepustowości programu do cieniowania przepływności i pamięci, należy rozważyć użycie filtrowanie anizotropowe, aby osiągnąć najlepsze obrazu jakość w swojej aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Warianty te zastąpienia stany próbkowania na wywołania `ID3D11DeviceContext::PSSetSamplers` w tryb filtru próbnika aplikacji — pod warunkiem czyli jeden z nich:  
  
- `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_ANISOTROPIC`  
  
  W **filtrowania tekstur punktu** typu variant, tryb filtru dostarczane do aplikacji jest zastępowany `D3D11_FILTER_MIN_MAG_MIP_POINT`; w **warianty punktowego filtrowania tekstur** typu variant, zostaje zastąpiony `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`; a następnie w **Trójliniowego filtrowania tekstur** typu variant, zostaje zastąpiony `D3D11_FILTER_MIN_MAG_MIP_LINEAR`.  
  
  W **Anizotropowego filtrowania tekstur** typu variant, tryb filtru dostarczane do aplikacji jest zastępowany `D3D11_FILTER_ANISOTROPIC`, a Anisotropy maksymalna jest ustawiona na 16.  
  
## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia  
 W interfejsie Direct3D poziom funkcji 9.1 określa maksymalny anisotropy 2 x. Ponieważ **Anizotropowego filtrowania tekstur** wariant odwołuje się do 16 x anisotropy wyłącznie, odtwarzanie zakończy się niepowodzeniem, gdy analiza klatek jest uruchamiana na urządzeniu 9.1 poziomu funkcji. Współczesne urządzeń, których dotyczy to ograniczenie obejmują tabletów Surface RT i Windows 2 powierzchni oparte na ARM. Starsze procesory GPU może nadal można je znaleźć w niektórych komputerów może mieć wpływ, ale są powszechnie uznawane za przestarzałe i są coraz bardziej rzadko.  
  
## <a name="example"></a>Przykład  
 **Filtrowania tekstur punktu** wariant zostać odtworzone przy użyciu kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Przykład  
 **Warianty punktowego filtrowania tekstur** wariant zostać odtworzone przy użyciu kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Przykład  
 **Trójliniowego filtrowania tekstur** wariant zostać odtworzone przy użyciu kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Przykład  
 **Anizotropowego filtrowania tekstur** wariant zostać odtworzone przy użyciu kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```



