---
title: Wariant formatu docelowego renderowania 16bpp | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157568"
---
# <a name="16bpp-render-target-format-variant"></a>Wariant formatu docelowego renderowania 16bpp
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawia format pikseli do DXGI_FORMAT_B5G6R5_UNORM dla wszystkich elementów docelowych renderowania i buforów zwrotnych.  
  
## <a name="interpretation"></a>Interpretacja  
 Obiekt docelowy renderowania lub bufor zapasowy zwykle używa formatu 32bpp (32 bitów na piksel), takiego jak B8G8R8A8_UNORM. formaty 32bpp mogą zużywać dużą przepustowość pamięci. Ponieważ format B5G6R5_UNORM to format 16bpp o rozmiarze połówkowym w formatach 32bpp, przy użyciu którego można zwolnić obciążenie przepustowości pamięci, ale kosztem zmniejszenia dokładności koloru.  
  
 Jeśli ten wariant pokazuje duży wzrost wydajności, prawdopodobnie wskazuje, że aplikacja zużywa zbyt dużą przepustowość pamięci. Zwiększenie wydajności może być szczególnie zauważalne, gdy profilowana ramka pogorszy się ze znaczną ilością narysowania lub zawiera wiele z mieszania alfa.  
  
 Jeśli rodzaje scen, które są renderowane przez aplikację, nie wymagają odtwarzania kolorów o wysokiej wierności, nie wymagają, aby obiekt docelowy renderowania miał kanał alfa i nie zawierał często gładkich gradientów — które są podatne na przedziały między artefaktami w zmniejszonej dokładności koloru — Rozważ użycie formatu docelowego renderowania 16bpp w celu zmniejszenia użycia przepustowości pamięci.  
  
 Jeśli sceny, które są renderowane w aplikacji, wymagają odtworzenia kolorów o wysokiej wierności lub kanału alfa, lub płynne gradienty są wspólne, należy wziąć pod uwagę inne strategie zmniejszania użycia przepustowości pamięci — na przykład zmniejszenie ilości danych narysowanych lub mieszanych, zmniejszenie wymiarów bufor ramki lub zmodyfikowanie zasobów tekstury w celu użycia mniejszej przepustowości pamięci przez włączenie kompresji lub zmniejszenie ich wymiarów. Jak zwykle należy wziąć pod uwagę jakość obrazu, która jest dostarczana z dowolnymi z tych optymalizacji.  
  
 Jeśli aplikacja będzie mogła korzystać z przełączenia do 16bppego buforu, ale jest częścią łańcucha wymiany, należy wykonać dodatkowe czynności, ponieważ DXGI_FORMAT_B5G6R5_UNORM nie jest obsługiwanym formatem buforu w przypadku łańcuchów wymiany utworzonych przy użyciu `D3D11CreateDeviceAndSwapChain` lub `IDXGIFactory::CreateSwapChain` . Zamiast tego należy utworzyć obiekt docelowy renderowania formatu B5G6R5_UNORM przy użyciu funkcji `CreateTexture2D` i renderowania do tego elementu. Następnie przed wywołaniem w łańcuchu wymiany Skopiuj obiekt docelowy renderowania do buforu zapasowego łańcucha wymiany, rysując pełny ekran cztery z obiektem docelowym renderowania jako teksturą źródłową. Chociaż jest to dodatkowy krok, który będzie zużywał pewną przepustowość pamięci, większość operacji renderowania zużywa mniejszą przepustowość, ponieważ wpływają one na obiekt docelowy renderowania 16bpp. Jeśli spowoduje to zaoszczędzenie większej przepustowości niż jest używana przez skopiowanie elementu docelowego renderowania do buforu zapasowego łańcucha wymiany, zwiększona wydajność renderowania.  
  
 Architektury procesora GPU korzystające z wieloskładnikowych technik renderowania mogą uzyskać znaczne korzyści z wydajności przy użyciu formatu 16bpp bufor ramki, ponieważ większa część bufor ramki może pasować do lokalnej pamięci podręcznej bufor ramki każdej kafelka. Wbudowane architektury renderowania są czasami dostępne w procesorach GPU na urządzeniach przenośnych i komputerach typu Tablet. rzadko są one wyświetlane poza tym Niszem.  
  
## <a name="remarks"></a>Uwagi  
 Format elementu docelowego renderowania jest resetowany do DXGI_FORMAT_B5G6R5_UNORM przy każdym wywołaniu do `ID3D11Device::CreateTexture2D` , który tworzy obiekt docelowy renderowania. W odróżnieniu od tego, jaki format jest zastępowany, gdy obiekt D3D11_TEXTURE2D_DESC przeszedł w pDesc, opisuje element docelowy renderowania; Czyli:  
  
- Element członkowski BindFlags ma ustawioną flagę D3D11_BIND_REDNER_TARGET.  
  
- Element członkowski BindFlags ma wyczyszczoną flagę D3D11_BIND_DEPTH_STENCIL.  
  
- Element członkowski użycia jest ustawiony na D3D11_USAGE_DEFAULT.  
  
## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia  
 Ponieważ format B5G6R5 nie zawiera kanału alfa, zawartość alfa nie jest zachowywana przez ten wariant. Jeśli renderowanie aplikacji wymaga kanału alfa w obiekcie docelowym renderowania, nie można po prostu przełączyć się do formatu B5G6R5.  
  
## <a name="example"></a>Przykład  
 Wariant **formatu docelowego renderowania 16bpp** można odtworzyć dla elementów docelowych renderowania utworzonych za pomocą przy użyciu `CreateTexture2D` kodu w następujący sposób:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
