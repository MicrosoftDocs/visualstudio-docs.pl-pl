---
title: Wariant rozmiaru okienka ekranu 1 x 1 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 74e3bc706cb2df12aacddf9fbb77dec598bfc17a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757903"
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
