---
title: 16bpp renderowania wariant formatu docelowego | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab58cbcd6644d540b7db2efb1cad59e5d80f8530
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986664"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bpp renderowania wariant formatu docelowego
Zestawy piksel formatu DXGI_FORMAT_B5G6R5_UNORM wszystkie elementy docelowe renderowania i Utwórz kopię buforów.  
  
## <a name="interpretation"></a>Interpretacja  
 Obiektu docelowego renderowania lub buforu zapasowego zwykle korzysta z formatu bpp 32 (32 bity na piksel), takie jak B8G8R8A8_UNORM. formaty 32 bpp może zużywać dużą ilość pamięci przepustowość. Ponieważ B5G6R5_UNORM format formacie 16 bpp, który jest połowa formatów 32 bpp, korzystania z niego można zwolnić wykorzystanie przepustowości pamięci, ale kosztem mniejsze koloru.  
  
 Jeśli ten wariant wykazuje duże są bardziej wydajne, prawdopodobnie oznacza to, że aplikacja zużywa zbyt dużej ilości pamięci przepustowość. Możesz uzyskać poprawy istotnie poprawiającą wydajność, szczególnie w przypadku ramek profilowanej była znacząca ilość overdraw lub używanie mieszania alfa.

16-bpp formatu docelowego renderowania może zmniejszyć pasmo pamięci z użyciem, gdy Twoja aplikacja ma następujące warunki:
- Nie wymaga odtwarzania o dużej wierności kolorów.
- Nie wymaga kanału alfa.
- Nie ofent ma gradientów smooth, (które są podatne na przedziały artefaktów w ograniczonym koloru).

Inne strategie w celu zmniejszenia obciążenia przepustowości pamięci obejmują:
- Zmniejsz ilość overdraw lub używanie mieszania alfa.
- Zmniejsz wymiary buforu ramki.
- Zmniejsz wymiary zasobów tekstur.
- Zmniejsz kompresji zasobów tekstur.
 
W zwykły sposób należy wziąć pod uwagę obraz jakości wad i zalet, które pochodzą z dowolną z tych optymalizacjach.  

Aplikacje, które są częścią łańcucha wymiany mają format buforu zapasowego (DXGI_FORMAT_B5G6R5_UNORM), który nie obsługuje 16 bpp. Te łańcuchy wymiany są tworzone za pomocą `D3D11CreateDeviceAndSwapChain` lub `IDXGIFactory::CreateSwapChain`. Aby obejść to ograniczenie, wykonaj następujące czynności:
1. Tworzenie elementu docelowego renderowania format B5G6R5_UNORM przy użyciu `CreateTexture2D` i renderowania do obiektu docelowego. 
2. Kopiowanie obiektu docelowego renderowania na buforu zapasowego łańcucha wymiany w celu za pomocą rysowania cztery pełnego ekranu, za pomocą obiektu docelowego renderowania jako swoje źródła tekstury.
3. Wywołują metody Present na swój łańcuch wymiany.

   Jeśli ta strategia zapisuje większą przepustowość niż jest wykorzystywane przez skopiowanie obiektu docelowego renderowania buforu zapasowego łańcucha wymiany w celu, jest lepsza wydajność renderowania.

   Architektury procesora GPU, korzystające z techniki fragmentacji renderowania można zobaczyć korzystny wydajności przy użyciu formatu buforu ramki 16 bpp. To ulepszenie jest, ponieważ większą część buforu ramki mieści się w pamięci podręcznej buforu ramki lokalnego każdego kafelka. Renderowanie fragmentacji architektury czasami znajdują się w procesorach GPU znajdujących się w aparaty telefoniczne przenośnych i komputerów typu tablet. rzadko pojawiają się one poza tym niche.  
  
## <a name="remarks"></a>Uwagi  
 Format docelowy renderowania jest resetowana do DXGI_FORMAT_B5G6R5_UNORM na każde wywołanie `ID3D11Device::CreateTexture2D` tworząca docelowego renderowania. W szczególności format jest zastępowany podczas przekazany pDesc obiekt D3D11_TEXTURE2D_DESC opisuje cel renderowania; Czyli:  
  
-   Element członkowski BindFlags ma flagę D3D11_BIND_REDNER_TARGET zestawu.  
  
-   Element członkowski BindFlags ma flagę D3D11_BIND_DEPTH_STENCIL wyczyszczone.  
  
-   Użycie elementu członkowskiego jest równa D3D11_USAGE_DEFAULT.  
  
## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia  
 Ponieważ B5G6R5 format nie ma kanału alfa, alfa zawartości nie są zachowywane przez ten typ variant. Jeśli renderowanie aplikacji wymaga kanał alfa w docelowych renderowania, po prostu nie można przełączyć do formatu B5G6R5.  
  
## <a name="example"></a>Przykład  
 **16 bpp formatu docelowego renderowania** wariant można odtworzyć dla obiektów docelowych renderowania utworzone za pomocą `CreateTexture2D` przy użyciu kodu w następujący sposób:  
  
```cpp
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
