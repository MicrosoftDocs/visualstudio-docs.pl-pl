---
title: Wariant formatu docelowego renderowania 16bpp | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a63261a4ef8a6304bec8c2bdde1d9ec9113405e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74188590"
---
# <a name="16-bpp-render-target-format-variant"></a>Wariant formatu docelowego renderowania BPP
Ustawia format pikseli do DXGI_FORMAT_B5G6R5_UNORM dla wszystkich elementów docelowych renderowania i buforów zwrotnych.

## <a name="interpretation"></a>Interpretacja
 Obiekt docelowy renderowania lub bufor zapasowy zwykle używa formatu 32 BPP (32 bitów na piksel), takiego jak B8G8R8A8_UNORM. 32 — formaty BPP mogą zużywać dużą ilość pamięci. Ponieważ format B5G6R5_UNORM to format 16-BPP, który ma połowę rozmiaru formatów 32-BPP, za pomocą którego można zwolnić obciążenie przepustowości pamięci, ale kosztem zmniejszenia dokładności koloru.

 Jeśli ten wariant pokazuje duży wzrost wydajności, prawdopodobnie wskazuje, że aplikacja zużywa zbyt dużą przepustowość pamięci. Możesz uzyskać znaczne zwiększenie wydajności, szczególnie gdy profilowana ramka miała znaczną ilość narysowania lub przenikania alfa.

Format docelowy renderowania 16 BPP umożliwia zmniejszenie pasma pamięci przy użyciu, gdy aplikacja ma następujące warunki:
- Nie wymaga odtwarzania kolorów o wysokiej wierności.
- Nie wymaga kanału alfa.
- Nie ma często gładkich gradientów (które są podatne na przedziały między artefaktami w zmniejszonej dokładności koloru).

Inne strategie zmniejszania przepustowości pamięci obejmują:
- Zmniejsz ilość narysowania lub mieszania alfa.
- Zmniejsz wymiary buforu ramek.
- Zmniejsz wymiary zasobów tekstury.
- Zmniejszenie kompresji zasobów tekstury.

Jak zwykle należy wziąć pod uwagę jakość obrazu, która jest dostarczana z dowolnymi z tych optymalizacji.

Aplikacje, które są częścią łańcucha wymiany mają format buforu zapasowego (DXGI_FORMAT_B5G6R5_UNORM), który nie obsługuje 16 BPP. Te łańcuchy wymiany są tworzone przy użyciu `D3D11CreateDeviceAndSwapChain` lub `IDXGIFactory::CreateSwapChain` . Aby obejść to ograniczenie, wykonaj następujące czynności:
1. Utwórz obiekt docelowy renderowania w formacie B5G6R5_UNORM za pomocą `CreateTexture2D` i Renderuj do tego obiektu docelowego.
2. Skopiuj obiekt docelowy renderowania do buforu wielowymiarowego łańcucha wymiany, rysując pełny ekran cztery z obiektem docelowym renderowania jako teksturą źródłową.
3. Wywołanie obecne w łańcuchu wymiany.

   Jeśli ta strategia oszczędza większą przepustowość niż jest używana przez skopiowanie elementu docelowego renderowania do buforu zapasowego łańcucha wymiany, zwiększona wydajność renderowania.

   Architektury procesora GPU korzystające ze stosujących się technik renderowania mogą uzyskać znaczący wpływ na wydajność przy użyciu 16 BPP formatu bufora klatek. To ulepszenie wynika z faktu, że większa część buforu ramki może pasować do lokalnej pamięci podręcznej buforu ramki każdego kafelka. Wbudowane architektury renderowania są czasami dostępne w procesorach GPU na urządzeniach przenośnych i komputerach typu Tablet. rzadko są one wyświetlane poza tym Niszem.

## <a name="remarks"></a>Uwagi
 Format elementu docelowego renderowania jest resetowany do DXGI_FORMAT_B5G6R5_UNORM przy każdym wywołaniu do `ID3D11Device::CreateTexture2D` , który tworzy obiekt docelowy renderowania. W odróżnieniu od tego, jaki format jest zastępowany, gdy obiekt D3D11_TEXTURE2D_DESC przeszedł w pDesc, opisuje element docelowy renderowania; Czyli:

- Element członkowski BindFlags ma ustawioną flagę D3D11_BIND_REDNER_TARGET.

- Element członkowski BindFlags ma wyczyszczoną flagę D3D11_BIND_DEPTH_STENCIL.

- Element członkowski użycia jest ustawiony na D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia
 Ponieważ format B5G6R5 nie zawiera kanału alfa, zawartość alfa nie jest zachowywana przez ten wariant. Jeśli renderowanie aplikacji wymaga kanału alfa w obiekcie docelowym renderowania, nie można po prostu przełączyć się do formatu B5G6R5.

## <a name="example"></a>Przykład
 Wariant **formatu docelowego renderowania 16 BPP** można odtworzyć dla elementów docelowych renderowania utworzonych za pomocą przy użyciu `CreateTexture2D` kodu w następujący sposób:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
