---
title: Wariant generowania mip-map | Microsoft Docs
description: Jeśli generowanie mip-map pokazuje duży wzrost wydajności, oznacza to, że używasz tekstur bez włączania mip-maps i nie uzyskujesz jak najwięcej z pamięci podręcznej tekstur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e17981b819ccc719399a6ed14071615f2deb54a
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232443"
---
# <a name="mip-map-generation-variant"></a>Wariant generowania mipmapy
Włącza mip-maps na teksturach, które nie są celami renderowania.

## <a name="interpretation"></a>Interpretacja
Mip-maps są używane głównie do eliminowania aliasów artefaktów w teksturach w ramach minyfikacji przez wstępne obliczenie mniejszych wersji tekstury. Mimo że te dodatkowe tekstury zużywają pamięć procesora GPU — około 33% więcej niż oryginalna tekstura — są również bardziej wydajne, ponieważ więcej obszarów powierzchni mieści się w pamięci podręcznej tekstur procesora GPU, a jego zawartość osiąga wyższe wykorzystanie.

W przypadku scen 3D zalecamy użycie map mip,gdy jest dostępna pamięć do przechowywania dodatkowych tekstur, ponieważ zwiększają one wydajność renderowania i jakość obrazu.

Jeśli ten wariant pokazuje znaczący wzrost wydajności, oznacza to, że używasz tekstur bez włączania mip-maps, a tym samym nie korzystasz w jak najwięcej z pamięci podręcznej tekstur.

## <a name="remarks"></a>Uwagi
Generowanie mapy Mip jest wymuszane przy każdym wywołaniu do `ID3D11Device::CreateTexture2D` , które tworzy teksturę źródłową. W szczególności generowanie mip-map jest wymuszane, gdy przekazany D3D11_TEXTURE2D_DESC obiekt cieniowania opisuje niezmieniony zasób `pDesc` modułu cieniującego, czyli:

- Członek BindFlags ma tylko D3D11_BIND_SHADER_RESOURCE flagi.

- Członek Użycie jest ustawiony na wartość D3D11_USAGE_DEFAULT lub D3D11_USAGE_IMMUTABLE.

- Członek CPUAccessFlags jest ustawiony na 0 (bez dostępu do procesora CPU).

- Członek SampleDesc ma swój członek Count ustawiony na 1 (brak wielo sample anti-aliasing (MSAA)).

- Dla członka mipLevels ustawiono wartość 1 (brak istniejącej mapy mip).

  Gdy dane początkowe są dostarczane przez aplikację, format tekstury musi obsługiwać automatyczne generowanie mapy mip — zgodnie z D3D11_FORMAT_SUPPORT_MIP_AUTOGEN — chyba że format to BC1, BC2 lub BC3; W przeciwnym razie tekstura nie jest modyfikowana i po podano początkowe dane nie są generowane żadne mapy mip.

  Jeśli mapy mip zostały wygenerowane automatycznie dla tekstury, wywołania funkcji są modyfikowane podczas odtwarzania w celu użycia `ID3D11Device::CreateShaderResourceView` łańcucha mip podczas próbkowania tekstury.

## <a name="example"></a>Przykład
Wariant **generowania mapy Mip** można odtworzyć przy użyciu kodu w ten sposób:

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

Aby utworzyć teksturę z pełnym łańcuchem mip, ustaw `D3D11_TEXTURE2D_DESC::MipLevels` wartość 0. Liczba poziomów mip w pełnym łańcuchu mip to floor(log2(n) + 1), gdzie n jest największym wymiarem tekstury.

Pamiętaj, że po podaniem początkowych danych do usługi należy podać `CreateTexture2D` D3D11_SUBRESOURCE_DATA dla każdego poziomu mip.

> [!NOTE]
> Jeśli chcesz udostępnić własną zawartość na poziomie mip zamiast generować je automatycznie, musisz utworzyć tekstury przy użyciu edytora obrazów, który obsługuje tekstury mapowane przez mip, a następnie załadować plik i przekazać poziomy mip do `CreateTexture2D` .

## <a name="see-also"></a>Zobacz też
[Wariant wymiarów połowy/ćwiartki tekstury](half-quarter-texture-dimensions-variant.md)
