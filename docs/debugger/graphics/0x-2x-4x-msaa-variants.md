---
title: 0 wariantów x-2 x-4 x MSAA | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3877988376c21425777beed628edd7fbdeed21e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985975"
---
# <a name="0x2x4x-msaa-variants"></a>0 x / 2 x / 4 x MSAA wariantów
Zastąpienia wielu przykładowe Wygładzanie (MSAA) ustawień dla wszystkich elementy docelowe renderowania i łańcuchy wymiany.  
  
## <a name="interpretation"></a>Interpretacja  
 Wielu przykładowe wygładzanie zwiększa jakość wizualną, pobieranie próbek w wielu lokalizacjach w każdego piksela; wyższy poziom MSAA zajmuje więcej przykładów i bez MSAA, tylko jeden przykład pochodzi z centrum piksela. Włączanie MSAA w swojej aplikacji, zwykle ma niewielkie ale zauważalne koszt wydajności renderowania, ale w niektórych obciążeń lub na niektórych procesorach GPU znajdujących się, może być miał prawie bez wpływu.  
  
 Jeśli Twoja aplikacja ma już włączoną MSAA, mniejsze wariantów MSAA wskazują koszt względnej wydajności, która ponosi MSAA istniejących, wyższego poziomu. W szczególności 0 wariant x MSAA wskazuje względną wydajność aplikacji bez MSAA.  
  
 Jeśli aplikacja nie ma jeszcze MSAA włączone, 2 x MSAA i 4 wariantów x MSAA wskazują koszt względnej wydajności umożliwiające im w swojej aplikacji. Gdy koszt jest zadowalająco niski, należy rozważyć włączenie MSAA zwiększyć jakość obrazu aplikacji.  
  
> [!NOTE]
>  Sprzęt nie może w pełni obsługuje MSAA we wszystkich formatach. Ograniczenie sprzętu, który nie pracuje w całym wszystkich tych wariantów wystąpienia, kolumny w tabeli podsumowania wydajności jest pusta i jest generowany komunikat o błędzie.  
  
## <a name="remarks"></a>Uwagi  
 Te wariantów Zastąp przykładowe jakość próbkowania i liczba argumentów dla wywołań `ID3DDevice::CreateTexture2D` które tworzą elementy docelowe renderowania. W szczególności te parametry zostaną zastąpione, gdy:  
  
- `D3D11_TEXTURE2D_DESC` Obiekt przekazany w `pDesc` opisuje obiekt docelowy renderowania; który jest:  
  
  -   Element członkowski BindFlags ma flagę D3D11_BIND_TARGET albo ustawiona jest flaga D3D11_BIND_DEPTH_STENCIL.  
  
  -   Użycie elementu członkowskiego jest równa D3D11_USAGE_DEFAULT.  
  
  -   Element członkowski CPUAccessFlags jest równa 0.  
  
  -   Element członkowski MipLevels jest ustawiona na 1.  
  
- Urządzenie obsługuje liczność próbki żądanej (0, 2 lub 4) i jakość próbkowania (0) dla żądanego docelowej format (członek D3D11_TEXTURE2D_DESC::Format), zgodnie z ustaleniami renderowania `ID3D11Device::CheckMultisampleQualityLevels`.  
  
  Jeśli element członkowski D3D11_TEXTURE2D_DESC::BindFlags ma D3D_BIND_SHADER_RESOURCE lub D3D11_BIND_UNORDERED_ACCESS flag ustawionych, są tworzone dwie wersje tekstury; pierwszy ma tych flag wyczyszczone do użycia jako obiektu docelowego renderowania, a drugi to teksturę bez MSAA, która ma te flagi niezmienione może pełnić rolę bufora rozwiązania dla pierwszej wersji. Jest to konieczne, ponieważ prawdopodobnie nie będzie obowiązywać przy użyciu tekstury MSAA jako zasób programu do cieniowania lub nieuporządkowanego dostępu — na przykład programu do cieniowania, działające na nim będzie wygenerować niepoprawne wyniki, ponieważ go oczekiwać tekstury bez MSAA. Jeśli wariant utworzył tekstury dodatkowej bez MSAA, następnie zawsze wtedy, gdy cel renderowania MSAA usunięta z kontekstu urządzenia, jego zawartość są rozwiązywane do tekstury bez MSAA. Podobnie zawsze wtedy, gdy renderowania MSAA docelowy powinien zostać powiązany jako zasób programu do cieniowania lub jest używany w widok nieuporządkowanego dostępu, tekstury rozwiązany bez MSAA jest powiązana zamiast tego.  
  
  Te wariantów również zastąpienia ustawień MSAA wszystkie łańcuchy wymiany utworzone za pomocą `IDXGIFactory::CreateSwapChain`, `IDXGIFactory2::CreateSwapChainForHwnd`, `IDXGIFactory2::CreateSwapChainForCoreWindow`, `IDXGIFactory2::CreateSwapChainForComposition`, i `ID3D11CreateDeviceAndSwapChain`.  
  
  Net te zmiany powoduje, że renderowanie wszystkich odbywa się do obiektu docelowego renderowania MSAA, ale jeśli aplikacja używa jednej z tych renderowania elementów docelowych lub łańcucha wymiany buforów jako widok zasobów programu do cieniowania lub widok nieuporządkowanego dostępu, a następnie próbkowania danych z rozwiązania , bez MSAA kopię obiektu docelowego renderowania.  
  
## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia  
 W Direct3D11 MSAA tekstury są bardziej ograniczony w innych MSAA tekstury. Na przykład nie można wywołać `ID3D11DeviceContext::UpdateSubresource` MSAA tekstury i wywoływania `ID3D11DeviceContext::CopySubresourceRegion` zakończy się niepowodzeniem, jeśli liczba próbek i jakość próbkowania zasobu źródłowego i docelowego zasobu nie są zgodne, które mogą wystąpić, gdy ten wariant zastępuje ustawienia MSAA jednej zasób, ale nie drugiej.  
  
 Podczas odtwarzania wykryje te rodzaje konfliktów, zapewnia najlepszy nakład pracy w celu replikowania zamierzonego zachowania, ale nie może nie być możliwe do jego wyniki są identyczne. Chociaż jest to nietypowe, to wpłynąć na działanie tych warianty w taki sposób, że zniesławiającej ich wpływ, jest możliwe — na przykład, gdy sterowanie przepływem w program do cieniowania pikseli jest określana przez dokładnej zawartości tekstury — ponieważ replikowane tekstury może nie mieć identyczną zawartość.  
  
## <a name="example"></a>Przykład  
 Te wariantów, można odtworzyć dla obiektów docelowych renderowania utworzone za pomocą `ID3D11Device::CreateTexture2D` przy użyciu kodu w następujący sposób:  
  
```cpp
D3D11_TEXTURE2D_DESC target_description;  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
target_description.SampleDesc.Quality = 0;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```  
  
## <a name="example"></a>Przykład  
 Lub łańcuchy wymiany utworzone za pomocą IDXGISwapChain::CreateSwapChain lub D3D11CreateDeviceAndSwapChain przy użyciu kodu w następujący sposób:  
  
```cpp
DXGI_SWAP_CHAIN_DESC chain_description;  
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
chain_description.SampleDesc.Quality = 0;  
  
// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.  
```
