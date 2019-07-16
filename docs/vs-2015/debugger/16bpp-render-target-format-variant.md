---
title: 16bpp renderowania wariant formatu docelowego | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b315c7ab9bb10d039e81ba26b1beb9c4447a205
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157568"
---
# <a name="16bpp-render-target-format-variant"></a>Wariant formatu docelowego renderowania 16bpp
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestawy piksel formatu DXGI_FORMAT_B5G6R5_UNORM wszystkie elementy docelowe renderowania i Utwórz kopię buforów.  
  
## <a name="interpretation"></a>Interpretacja  
 Obiektu docelowego renderowania lub buforu zapasowego zazwyczaj używa formatu B8G8R8A8_UNORM: 32 bitowej (32 bity na piksel). formaty 32 bitowej może zajmować dużo pamięci przepustowości. Ponieważ B5G6R5_UNORM format formacie 16bpp rozmiarze 32 bitowej formatów, korzystania z niego można zwolnić wykorzystanie przepustowości pamięci, ale kosztem mniejsze koloru.  
  
 Jeśli ten wariant wykazuje duże są bardziej wydajne, prawdopodobnie oznacza to, że aplikacja zużywa zbyt dużej ilości pamięci przepustowość. Wzrost wydajności mogą szczególnie występować w przypadku ramek profilowanej odczuwa znacznej ilości overdraw lub zawiera wiele przenikaniem alfa.  
  
 Jeśli rodzaje scen, które są renderowane przez aplikację nie wymagają odtwarzania o dużej wierności kolorów, nie wymagają obiektu docelowego renderowania mieć kanał alfa, a często nie zawierają smooth gradientów — nadają się do pominiętym artefaktów w ograniczonym kolorów wierności — należy wziąć pod uwagę przy użyciu formatu docelowego renderowania 16bpp w celu zmniejszenia użycia przepustowości pamięci.  
  
 Jeśli scen, które są renderowane w aplikacji wymagają odtwarzania o dużej wierności kolorów lub kanał alfa, lub smooth gradientów są wspólne, należy wziąć pod uwagę inne strategie w celu zmniejszenia użycia przepustowości pamięci — na przykład skrócenie overdraw lub przenikaniem alfa zmniejszenie wymiarów obiektu lub modyfikowania zasobów tekstur z mniejszej przepustowości pamięci przez włączenie kompresji lub zmniejszając wymiarami. W zwykły sposób należy wziąć pod uwagę obraz jakości wad i zalet, które pochodzą z dowolną z tych optymalizacjach.  
  
 Jeśli aplikacja używającym przełączanie do buforu zapasowego 16bpp, ale jest częścią swój łańcuch wymiany, należy wykonać dodatkowe czynności, ponieważ nie jest DXGI_FORMAT_B5G6R5_UNORM format obsługiwanych buforu zapasowego łańcucha wymiany utworzone za pomocą `D3D11CreateDeviceAndSwapChain` lub `IDXGIFactory::CreateSwapChain`. Zamiast tego należy utworzyć cel B5G6R5_UNORM format renderowania przy użyciu `CreateTexture2D` i renderowania, zamiast tego. Następnie przed na swój łańcuch wymiany wywołują metody Present, skopiuj docelowego renderowania na buforu zapasowego łańcucha wymiany w celu za pomocą rysowania cztery pełnego ekranu, za pomocą obiektu docelowego renderowania jako swoje źródła tekstury. Chociaż jest to dodatkowego kroku spowoduje zmniejszenia przepustowości przez niektórych pamięci, większość operacji renderowania zużyje mniejszej przepustowości, ponieważ mają one wpływ na obiektu docelowego renderowania 16bpp; Jeśli spowoduje to zapisanie większą przepustowość niż jest wykorzystywane przez skopiowanie obiektu docelowego renderowania buforu zapasowego łańcucha wymiany w celu, jest lepsza wydajność renderowania.  
  
 Architektury procesora GPU, korzystające z techniki fragmentacji renderowania można zobaczyć korzystny wydajności przy użyciu formatu bufor ramki 16bpp, ponieważ większą część bufor ramki mieści się w pamięci podręcznej lokalnej bufor ramki każdego kafelka. Renderowanie fragmentacji architektury czasami znajdują się w procesorach GPU znajdujących się w aparaty telefoniczne przenośnych i komputerów typu tablet. rzadko pojawiają się one poza tym niche.  
  
## <a name="remarks"></a>Uwagi  
 Format docelowy renderowania jest resetowana do DXGI_FORMAT_B5G6R5_UNORM na każde wywołanie `ID3D11Device::CreateTexture2D` tworząca docelowego renderowania. W szczególności format jest zastępowany podczas przekazany pDesc obiekt D3D11_TEXTURE2D_DESC opisuje cel renderowania; Czyli:  
  
- Element członkowski BindFlags ma flagę D3D11_BIND_REDNER_TARGET zestawu.  
  
- Element członkowski BindFlags ma flagę D3D11_BIND_DEPTH_STENCIL wyczyszczone.  
  
- Użycie elementu członkowskiego jest równa D3D11_USAGE_DEFAULT.  
  
## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia  
 Ponieważ B5G6R5 format nie ma kanału alfa, alfa zawartości nie są zachowywane przez ten typ variant. Jeśli renderowanie aplikacji wymaga kanał alfa w docelowych renderowania, po prostu nie można przełączyć do formatu B5G6R5.  
  
## <a name="example"></a>Przykład  
 **Formatu docelowego renderowania 16bpp** wariant można odtworzyć dla obiektów docelowych renderowania utworzone za pomocą `CreateTexture2D` przy użyciu kodu w następujący sposób:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
