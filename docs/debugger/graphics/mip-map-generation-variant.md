---
title: MIP — wariant generacji mapy | Microsoft Docs
description: Jeśli Generowanie mapy MCI pokazuje duże zyski z wydajności, oznacza to, że są używane tekstury bez włączania funkcji mapy MIP i nie jest to najbardziej najlepsze z pamięci podręcznej tekstury.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d939fb537ac6aed75d9b0f7bda2970a85f9175ad
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994970"
---
# <a name="mip-map-generation-variant"></a>Wariant generowania mipmapy
Włączenie MCI — odwzorowuje na tekstury, które nie są obiektami docelowymi.

## <a name="interpretation"></a>Interpretacja
MIP — mapy są używane przede wszystkim do eliminowania artefaktów aliasów w teksturach w obszarze minifikacja przez wstępne obliczenie mniejszych wersji tekstury. Chociaż te dodatkowe tekstury zużywają pamięć GPU — około 33% więcej niż oryginalna tekstura — są one również wydajniejsze, ponieważ większa część obszaru powierzchni mieści się w pamięci podręcznej tekstury procesora GPU, a jej zawartość uzyskuje wyższe wykorzystanie.

W przypadku scen trójwymiarowych zalecamy, aby mapy MIP były dostępne do przechowywania dodatkowych tekstur, ponieważ zwiększają one wydajność renderowania i jakość obrazu.

Jeśli ten wariant pokazuje znaczący wzrost wydajności, oznacza to, że są używane tekstury bez włączania funkcji mapy MIP i dlatego nie najlepiej korzystać z pamięci podręcznej tekstury.

## <a name="remarks"></a>Uwagi
MCI — Generowanie mapy jest wymuszane dla każdego wywołania `ID3D11Device::CreateTexture2D` , które tworzy teksturę źródłową. W odróżnieniu od tego, Generowanie mapy MIP jest wymuszane w przypadku, gdy obiekt D3D11_TEXTURE2D_DESC przeszedł w programie, `pDesc` zawiera opis niezmienionego zasobu programu do cieniowania.

- Element członkowski BindFlags ma tylko ustawioną flagę D3D11_BIND_SHADER_RESOURCE.

- Element członkowski użycia ma ustawioną wartość D3D11_USAGE_DEFAULT lub D3D11_USAGE_IMMUTABLE.

- Element członkowski CPUAccessFlags ma wartość 0 (brak dostępu procesora).

- Element członkowski SampleDesc ma ustawioną wartość 1 (bez wygładzania).

- Członek MipLevels ma ustawioną wartość 1 (brak istniejącej mapy MIP).

  Gdy dane początkowe są dostarczane przez aplikację, format tekstury musi obsługiwać automatyczne generowanie map MIP — zgodnie z D3D11_FORMAT_SUPPORT_MIP_AUTOGEN — chyba że format to BC1, BC2 lub BC3; w przeciwnym razie tekstura nie jest modyfikowana i żadne mapy MIP nie są generowane po dostarczeniu danych początkowych.

  Jeśli dla tekstury Wygenerowano automatycznie mapy MIP, wywołania `ID3D11Device::CreateShaderResourceView` są modyfikowane podczas odtwarzania, aby użyć łańcucha MIP podczas próbkowania tekstury.

## <a name="example"></a>Przykład
Wariantu **generowania mapy MIP** można odtworzyć przy użyciu kodu w następujący sposób:

```cpp
D3D11_TEXTURE2D_DESC texture_description;

// ...

texture_description.MipLevels = 0; // generate a full mipchain

std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);

for (auto&& mip_level : initial_data)
{
    // fill mip_level with the application-supplied initial data
}

d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)
```

Aby utworzyć teksturę, która ma pełny łańcuch MIP, ustaw wartość `D3D11_TEXTURE2D_DESC::MipLevels` 0. Liczba poziomów MIP w pełnym łańcuchu MIP jest podłogą (log2 — (n) + 1), gdzie n jest największym wymiarem tekstury.

Należy pamiętać, że w przypadku dostarczania początkowych danych do `CreateTexture2D` , należy dostarczyć D3D11_SUBRESOURCE_DATA obiektu dla każdego poziomu MCI.

> [!NOTE]
> Aby zapewnić własną zawartość poziomu MCI zamiast generować ją automatycznie, należy utworzyć tekstury przy użyciu edytora obrazów, który obsługuje tekstury mapowane na MCI, a następnie załadować plik i przekazać poziomy MCI do `CreateTexture2D` .

## <a name="see-also"></a>Zobacz też
[Wariant wymiarów tekstury połówkowej/Kwartałowej](half-quarter-texture-dimensions-variant.md)
