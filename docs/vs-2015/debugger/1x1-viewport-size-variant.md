---
title: 1x1 — wariant rozmiaru okienka ekranu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157553"
---
# <a name="1x1-viewport-size-variant"></a>Wariant rozmiaru 1x1 okienka ekranu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zmniejsza wymiary okienka ekranu dla wszystkich obiektów docelowych renderowania do 1x1 pikseli.  
  
## <a name="interpretation"></a>Interpretacja  
 Mniejszy okienko ekranu zmniejsza liczbę pikseli, które muszą być zacienione, ale nie zmniejsza liczby wierzchołków, które muszą zostać przetworzone. Ustawienie wymiarów okienka ekranu na 1x1 pikseli skutecznie eliminuje cieniowanie pikseli z aplikacji.  
  
 Jeśli ten wariant pokazuje duży wzrost wydajności, może to wskazywać, że aplikacja zużywa zbyt wiele fillrate. Może to wskazywać, że wybrana rozdzielczość jest zbyt duża dla platformy docelowej lub że Twoja aplikacja spędza znaczące piksele cieniowania czasu, które są później zastępowane. W wyniku tego sugeruje się, że zmniejszenie rozmiaru bufor ramki lub zmniejszenie ilości narysowania poprawi wydajność aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Wymiary okienka ekranu są resetowane do 1x1 pikseli po każdym wywołaniu `ID3D11DeviceContext::OMSetRenderTargets` lub `ID3D11DeviceContext::RSSetViewports` .  
  
## <a name="example"></a>Przykład  
 Ten wariant można odtworzyć przy użyciu kodu w następujący sposób:  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```
