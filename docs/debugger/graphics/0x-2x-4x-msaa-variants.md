---
title: Odmiany "0x-2x" 4x MSAA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e77c0d7b5cbba2faf73fcca85ffcd0db063d618e
ms.sourcegitcommit: 023f52f10fb91850824558478cbfd2ec965054f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94407552"
---
# <a name="0x2x4x-msaa-variants"></a>Warianty 0x/2x/4x MSAA
Przesłania wiele przykładowych ustawień wygładzania (MSAA) dla wszystkich obiektów docelowych renderowania i łańcuchów wymiany.

## <a name="interpretation"></a>Interpretacja
 Wiele prób wygładzania zwiększa jakość wizualną, pobierając próbki w wielu lokalizacjach w każdym pikselu; wyższe poziomy technologii MSAA pobierają więcej próbek i nie są MSAA, tylko jeden przykład jest pobierany z środka piksela. Włączenie technologii MSAA w aplikacji zwykle ma Nieumiarkowany, ale zauważalny koszt renderowania wydajności, ale pod pewnymi obciążeniami lub w niektórych procesorach GPU może mieć prawie Brak wpływu.

 Jeśli w aplikacji jest już włączona technologia MSAA, to mniejsze warianty MSAA wskazują na względny koszt wydajności, który jest używany przez istniejące, MSAA wyższego poziomu. W szczególności, zmienna MSAA "0x" oznacza względną wydajność aplikacji bez technologii MSAA.

 Jeśli Twoja aplikacja nie ma już włączonej technologii MSAA, a następnie różne odmiany MSAA i 4x, wybierz względny koszt wydajności, aby włączyć je w aplikacji. Gdy koszt jest zadowalająco niski, należy rozważyć włączenie technologii MSAA w celu zwiększenia jakości obrazu aplikacji.

> [!NOTE]
> Sprzęt może nie w pełni obsługiwać technologii MSAA dla wszystkich formatów. Jeśli którykolwiek z tych wariantów napotyka ograniczenie sprzętowe, którego nie można obejść, jego kolumna w tabeli Podsumowanie wydajności jest pusta i zostanie wyświetlony komunikat o błędzie.

## <a name="remarks"></a>Uwagi
 Te warianty przesłaniają liczbę próbek i argumenty jakości próbkowania dla wywołań `ID3DDevice::CreateTexture2D` , które tworzą elementy docelowe renderowania. Parametry te są zastępowane w następujących przypadkach:

- `D3D11_TEXTURE2D_DESC`Obiekt przeszedł w `pDesc` opisie elementu docelowego renderowania, czyli:

  - Element członkowski BindFlags ma ustawioną flagę D3D11_BIND_TARGET lub D3D11_BIND_DEPTH_STENCIL.

  - Element członkowski użycia jest ustawiony na D3D11_USAGE_DEFAULT.

  - Wartość elementu członkowskiego CPUAccessFlags jest równa 0.

  - Element członkowski MipLevels jest ustawiony na 1.

- Urządzenie obsługuje żądaną liczbę próbek (0, 2 lub 4) i jakość próbkowania (0) dla żądanego formatu docelowego renderowania (D3D11_TEXTURE2D_DESC:: format członkowski), zgodnie z definicją `ID3D11Device::CheckMultisampleQualityLevels` .

  Jeśli element członkowski D3D11_TEXTURE2D_DESC:: BindFlags ma ustawioną flagę D3D_BIND_SHADER_RESOURCE lub D3D11_BIND_UNORDERED_ACCESS, zostaną utworzone dwie wersje tekstury; pierwszy z tych flag został wyczyszczony do użycia jako obiekt docelowy renderowania, a druga to tekstura nieaktywna, która ma te flagi pozostawione nienaruszone, aby działać jako bufor rozpoznawania dla pierwszej wersji. Jest to konieczne, ponieważ użycie tekstury MSAA jako zasobu programu do cieniowania lub nieuporządkowanego dostępu jest mało prawdopodobne — na przykład, gdy cieniowanie działające w ten sposób będzie generować nieprawidłowe wyniki, ponieważ będzie oczekiwać tekstury niezgodnej ze standardem. Jeśli wariant utworzył dodatkową teksturę, która nie jest MSAA, wtedy, gdy obiekt docelowy renderowania MSAA nie zostanie ustawiony z kontekstu urządzenia, jego zawartość zostanie rozwiązany do tekstury niemsaa. Podobnie, zawsze, gdy obiekt docelowy renderowania MSAA powinien być powiązany jako zasób programu do cieniowania lub jest używany w widoku nieuporządkowanego dostępu, zamiast tego zostanie powiązana niezależna tekstura.

  Te warianty zastępują również ustawienia technologii MSAA we wszystkich łańcuchach wymiany utworzonych przy użyciu `IDXGIFactory::CreateSwapChain` , `IDXGIFactory2::CreateSwapChainForHwnd` , `IDXGIFactory2::CreateSwapChainForCoreWindow` , `IDXGIFactory2::CreateSwapChainForComposition` i `ID3D11CreateDeviceAndSwapChain` .

  Efektem netto tych zmian jest to, że wszystkie renderingi są wykonywane do obiektu docelowego renderowania MSAA, ale jeśli aplikacja używa jednego z tych elementów docelowych renderowania lub buforów wymiany, jako widoku zasobów programu do cieniowania lub widoku nieuporządkowanego dostępu, dane są pobierane z rozwiązanej, niezgodnej z nią kopii docelowej renderowania.

## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia
 W programie Direct3D11 tekstury MSAA są bardziej ograniczone niż tekstury niezgodne ze standardami. Na przykład nie można wywołać `ID3D11DeviceContext::UpdateSubresource` na teksturze MSAA i wywołanie `ID3D11DeviceContext::CopySubresourceRegion` kończy się niepowodzeniem, jeśli liczba próbek i jakość próbki zasobu źródłowego i zasobu docelowego nie są zgodne, co może wystąpić, gdy ten wariant zastępuje ustawienia MSAA jednego zasobu, ale nie drugi.

 Gdy odtwarzanie wykrywa te rodzaje konfliktów, najlepszym rozwiązaniem jest replikowanie zamierzonego zachowania, ale może nie być możliwe dokładne dopasowanie wyników. Chociaż zdarza się to w taki sposób, aby miało to wpływ na wydajność tych wariantów w sposób, który nie reprezentuje ich wpływu, jest to możliwe — na przykład gdy sterowanie przepływem w programie do cieniowania pikseli jest określane przez dokładną zawartość tekstury — ponieważ zreplikowana tekstura może nie mieć identycznej zawartości.

## <a name="example-1"></a>Przykład 1
 Te warianty mogą być odtwarzane dla elementów docelowych renderowania utworzonych za pomocą przy użyciu `ID3D11Device::CreateTexture2D` kodu w następujący sposób:

```cpp
D3D11_TEXTURE2D_DESC target_description;
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
target_description.SampleDesc.Quality = 0;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```

## <a name="example-2"></a>Przykład 2
 Lub w przypadku łańcuchów wymiany utworzonych przy użyciu IDXGISwapChain:: CreateSwapChain lub D3D11CreateDeviceAndSwapChain za pomocą kodu w następujący sposób:

```cpp
DXGI_SWAP_CHAIN_DESC chain_description;
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
chain_description.SampleDesc.Quality = 0;

// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.
```
