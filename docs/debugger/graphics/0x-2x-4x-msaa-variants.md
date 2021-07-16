---
title: Warianty 0x-2x-4x MSAA | Microsoft Docs
description: Dowiedz się, jak zastąpić ustawienia wielo sample anti-aliasing (MSAA) we wszystkich celach renderowania i łańcuchach zamiany przy użyciu wariantów 0x, 2x lub 4x MSAA.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 15cf6c257b54c8998b32213e7abf021b8b8ef816
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232638"
---
# <a name="0x2x4x-msaa-variants"></a>Warianty 0x/2x/4x MSAA
Zastępuje ustawienia wielo sample anti-aliasing (MSAA) dla wszystkich obiektów docelowych renderowania i łańcuchów zamiany.

## <a name="interpretation"></a>Interpretacja
 Wiele przykładowych anty aliasów zwiększa jakość wizualizacji, pobierając próbki w wielu lokalizacjach w każdym pikselu; Większe poziomy MSAA pobierają więcej próbek, a bez msAA tylko jedna próbka jest wyższa od środka piksela. Włączenie usługi MSAA w aplikacji zwykle ma niewielki, ale zauważalny koszt wydajności renderowania, ale w przypadku niektórych obciążeń lub niektórych procesorów GPU może mieć prawie żadnego wpływu.

 Jeśli aplikacja ma już włączoną usługę MSAA, mniejsze warianty MSAA wskazują względny koszt wydajności, który jest naliczany przez istniejącą usługę MSAA wyższego poziomu. W szczególności wariant 0x MSAA wskazuje względną wydajność aplikacji bez konta MSAA.

 Jeśli aplikacja nie ma jeszcze włączonej usługi MSAA, warianty 2x MSAA i 4x MSAA wskazują względny koszt wydajności włączania ich w aplikacji. Jeśli koszt jest akceptowalnie niski, rozważ włączenie usługi MSAA w celu poprawy jakości obrazu aplikacji.

> [!NOTE]
> Sprzęt może nie w pełni obsługiwać msaa dla wszystkich formatów. Jeśli którykolwiek z tych wariantów napotka ograniczenie sprzętowe, które nie może zostać zmienione, jego kolumna w tabeli podsumowania wydajności jest pusta i jest wyświetlany komunikat o błędzie.

## <a name="remarks"></a>Uwagi
 Te warianty zastępują liczbę próbek i argumenty jakości próbki dla wywołań, które `ID3DDevice::CreateTexture2D` tworzą obiekty docelowe renderowania. W szczególności te parametry są zastępowe, gdy:

- Przekazany `D3D11_TEXTURE2D_DESC` obiekt opisuje docelowy obiekt `pDesc` renderowania, czyli:

  - Członek BindFlags ma flagę D3D11_BIND_TARGET lub D3D11_BIND_DEPTH_STENCIL flagę.

  - Dla członka Usage (Użycie) ustawiono wartość D3D11_USAGE_DEFAULT.

  - CpuAccessFlags jest ustawiona na 0.

  - Dla członka MipLevels ustawiono wartość 1.

- Urządzenie obsługuje żądaną liczbę próbek (0, 2 lub 4) i jakość próbki (0) dla żądanego formatu docelowego renderowania (element członkowski D3D11_TEXTURE2D_DESC::Format), zgodnie z ustaleniami `ID3D11Device::CheckMultisampleQualityLevels` .

  Jeśli D3D11_TEXTURE2D_DESC::BindFlags ma D3D_BIND_SHADER_RESOURCE lub D3D11_BIND_UNORDERED_ACCESS flagi, tworzone są dwie wersje tekstury; Pierwszy ma te flagi wyczyszone do użycia jako obiekt docelowy renderowania, a drugi jest tekstury innych niż MSAA, który ma te flagi pozostawione bez zmian, aby działać jako bufor rozpoznawania dla pierwszej wersji. Jest to konieczne, ponieważ użycie tekstury MSAA jako zasobu cieniowania lub nieuporządkowany dostęp jest mało prawdopodobne, że będzie prawidłowy — na przykład działający na nim moduł cieniowania wygeneruje nieprawidłowe wyniki, ponieważ będzie oczekiwać tekstury innego niż MSAA. Jeśli wariant utworzył pomocniczą teksturę inny niż MSAA, za każdym razem, gdy obiekt docelowy renderowania MSAA nie zostanie wyzsetowany z kontekstu urządzenia, jego zawartość zostanie rozpoznana jako tekstura nieoczywiązana przez msaa. Podobnie za każdym razem, gdy obiekt docelowy renderowania MSAA powinien być powiązany jako zasób cieniowania lub jest używany w widoku nieuporządkowanym dostępu, zamiast tego powiązana jest rozpoznana tekstura nieuporządkowana MSAA.

  Te warianty zastępują również ustawienia MSAA we wszystkich łańcuchach wymiany utworzonych przy użyciu `IDXGIFactory::CreateSwapChain` elementów , , , i `IDXGIFactory2::CreateSwapChainForHwnd` `IDXGIFactory2::CreateSwapChainForCoreWindow` `IDXGIFactory2::CreateSwapChainForComposition` `ID3D11CreateDeviceAndSwapChain` .

  Efektem netto tych zmian jest to, że całe renderowanie jest wykonywane w celu renderowania MSAA, ale jeśli aplikacja używa jednego z tych elementów docelowych renderowania lub buforów łańcucha wymiany jako widoku zasobów cieniowania lub widoku nieuporządkowanych dostępu, dane są próbkowane z rozwiązanego, innego niż MSAA kopii obiektu docelowego renderowania.

## <a name="restrictions-and-limitations"></a>Ograniczenia
 W direct3D11 tekstury MSAA są bardziej ograniczone niż tekstury inne niż MSAA. Na przykład nie można wywołać metody na teksturze MSAA i wywołanie zakończy się niepowodzeniem, jeśli liczba próbek i jakość próbki zasobu źródłowego i docelowego nie są zgodne, co może wystąpić, gdy ten wariant zastąpi ustawienia MSAA jednego zasobu, ale nie `ID3D11DeviceContext::UpdateSubresource` `ID3D11DeviceContext::CopySubresourceRegion` drugiego.

 Gdy odtwarzanie wykrywa tego rodzaju konflikty, najlepszym rozwiązaniem jest replikowanie zamierzonego zachowania, ale dokładne dopasowanie wyników może nie być możliwe. Chociaż nierzadko ma to wpływ na wydajność tych wariantów w sposób, który błędnie przedstawia ich wpływ, jest możliwe — na przykład gdy sterowanie przepływem w programie do cieniowania pikseli jest określane przez precyzyjną zawartość tekstury — ponieważ replikowana tekstura może nie mieć identycznej zawartości.

## <a name="example-1"></a>Przykład 1
 Te warianty można odtworzyć dla obiektów docelowych renderowania utworzonych przy użyciu `ID3D11Device::CreateTexture2D` kodu takiego jak:

```cpp
D3D11_TEXTURE2D_DESC target_description;
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
target_description.SampleDesc.Quality = 0;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```

## <a name="example-2"></a>Przykład 2
 Można też użyć łańcuchów wymiany utworzonych przy użyciu identyfikatora IDXGISwapChain::CreateSwapChain lub D3D11CreateDeviceAndSwapChain przy użyciu kodu podobnego do tego:

```cpp
DXGI_SWAP_CHAIN_DESC chain_description;
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
chain_description.SampleDesc.Quality = 0;

// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.
```
