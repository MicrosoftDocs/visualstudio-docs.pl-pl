---
title: Wariant generowania mipmapy | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca094c4a29e18ebde5ac33f1c35c2a53d60c2327
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836546"
---
# <a name="mip-map-generation-variant"></a>Wariant generowania mipmapy
Umożliwia mapy mip na tekstury, które nie są renderowane elementów docelowych.  
  
## <a name="interpretation"></a>Interpretacja  
 Mapy MIP przede wszystkim są używane, aby wyeliminować artefaktów wygładzania w tekstury w obszarze minimalizację przez wstępne obliczanie mniejsze wersje tekstury. Mimo że te dodatkowe tekstury używa pamięci procesora GPU — około 33% wyższy niż oryginalnej tekstury — są one również bardziej efektywne, ponieważ jeden z ich powierzchni mieści się w pamięci podręcznej tekstury procesora GPU i jego zawartość osiągnięcia lepszego wykorzystania.  
  
 Dla scen 3D firma Microsoft zaleca mapy mip podczas za mało pamięci do przechowywania dodatkowych tekstury, ponieważ zwiększają wydajność renderowania i jakości obrazu.  
  
 Ten wariant przedstawiono istotne są bardziej wydajne, wskazuje, że używasz tekstury bez włączania mapy mip, a tym samym nie uzyskuje się maksymalnie dużo z pamięci podręcznej tekstury.  
  
## <a name="remarks"></a>Uwagi  
 Każde wywołanie jest wymuszana generacji mipmapy `ID3D11Device::CreateTexture2D` tworząca źródłową teksturę. W szczególności generacji mipmapy jest wymuszone, gdy D3D11_TEXTURE2D_DESC obiekt przekazany w `pDesc` opisuje niezmiennych zasób programu do cieniowania; będącego:  
  
- Element członkowski BindFlags ma tylko D3D11_BIND_SHADER_RESOURCE ustawiona jest flaga.  
  
- Użycie elementu członkowskiego jest równa D3D11_USAGE_DEFAULT lub D3D11_USAGE_IMMUTABLE.  
  
- Element członkowski CPUAccessFlags jest równa 0 (Brak dostępu Procesora).  
  
- Element członkowski SampleDesc ma członków liczba równa 1 (nie próbkowanie Wygładzanie (MSAA)).  
  
- Element członkowski MipLevels jest ustawiona na 1 (nie istniejącego mipmapy).  
  
  Gdy początkowe dane są dostarczane przez aplikację, format tekstury musi obsługiwać generacji mipmapy automatyczne — zgodnie z ustaleniami D3D11_FORMAT_SUPPORT_MIP_AUTOGEN — chyba, że format jest BC1, BC2 lub BC3; w przeciwnym razie Tekstura nie został zmodyfikowany i nie mapy mip są generowane, gdy początkowe dane są dostarczane.  
  
  Mapy mip zostały wygenerowane automatycznie tekstury, wywołania `ID3D11Device::CreateShaderResourceView` są modyfikowane podczas odtwarzania, aby korzystać z łańcucha mip w czasie pobierania próbek tekstury.  
  
## <a name="example"></a>Przykład  
 **Generacji mipmapy** wariant zostać odtworzone przy użyciu kodu w następujący sposób:  
  
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
  
 Aby utworzyć teksturę, która ma pełnego łańcucha mip, ustaw `D3D11_TEXTURE2D_DESC::MipLevels` na 0. Liczba poziomów mip w pełnego łańcucha mip jest: floor(log2(n) + 1), gdzie n to największy wymiarze tekstury.  
  
 Należy pamiętać, że jeśli podasz początkowej danych do `CreateTexture2D`, należy podać obiekt D3D11_SUBRESOURCE_DATA każdy poziom mip.  
  
> [!NOTE]
>  Jeśli chcesz podać własne mip poziomu zawartość zamiast generować je automatycznie, musi utworzyć swoje tekstury za pomocą obrazu edytora obsługującego mapowane mip tekstury i następnie załaduj plik i poziomów mip, aby przekazać `CreateTexture2D`.  
  
## <a name="see-also"></a>Zobacz też  
 [Wariant wymiarów jednej ósmej tekstury](half-quarter-texture-dimensions-variant.md)
