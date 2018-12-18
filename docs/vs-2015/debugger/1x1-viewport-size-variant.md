---
title: Wariant rozmiaru okienka ekranu 1 x 1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5280ed07d1799346b173ccac0f0186cd2bdca992
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777607"
---
# <a name="1x1-viewport-size-variant"></a>Wariant rozmiaru 1x1 okienka ekranu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Maksymalne wymiary okienka ekranu na wszystkie elementy docelowe renderowania na 1 x 1 pikseli.  
  
## <a name="interpretation"></a>Interpretacja  
 Mniejsze okienka ekranu zmniejsza liczbę pikseli, które muszą być przyciemnione, ale nie zmniejszyć liczbę wierzchołki, które muszą zostać przetworzone. Ustawienie wymiary okienka ekranu na 1 x 1 piksel skutecznie eliminuje cieniowania pikseli, z poziomu aplikacji.  
  
 Jeśli ten wariant wykazuje duże są bardziej wydajne, może to wskazywać, że aplikacja zużywa zbyt dużo fillrate. Może to oznaczać, że rozdzielczość wybrane jest zbyt duża dla platformy docelowej lub że aplikacja zużywa znaczną ilość czasu cieniowania pikseli, które później zostaną zastąpione (overdraw). Ten wynik zasugeruje, że zmniejszaniu rozmiaru obiektu użytkownika lub skrócenie overdraw poprawi wydajność Twojej aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Wymiary okienka ekranu są resetowane do pikseli 1 x 1 po każdym wywołaniu `ID3D11DeviceContext::OMSetRenderTargets` lub `ID3D11DeviceContext::RSSetViewports`.  
  
## <a name="example"></a>Przykład  
 Ten wariant zostać odtworzone przy użyciu kodu w następujący sposób:  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```



