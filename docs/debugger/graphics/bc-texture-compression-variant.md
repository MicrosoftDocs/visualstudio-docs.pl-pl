---
title: Wariant kompresji tekstury BC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5faf19632d746105deed3a36af6943627594175
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72736161"
---
# <a name="bc-texture-compression-variant"></a>Wariant kompresji tekstury BC
Włącza kompresję blokową dla tekstury, które mają format pikseli, który jest odmianą B8G8R8X8, B8G8R8A8 lub R8G8B8A8.

## <a name="interpretation"></a>Interpretacja
 Formaty kompresji oparte na blokach, takie jak BC1, BC2 i BC3 zajmują znacznie mniej pamięci niż nieskompresowane formaty obrazów i w związku z tym zużywają znacznie mniejszą przepustowość pamięci. W porównaniu z nieskompresowanym formatem, który używa 32 bitów na piksel, BC1 (dawniej znany jako DXT1) osiąga 8:1 kompresji i BC3 (dawniej znany jako DXT5) osiąga 4:1. Różnica między BC1 i BC3 polega na tym, że BC1 nie obsługuje kanału alfa, podczas gdy BC3 obsługuje kanał alfa skompresowany blokowo. Pomimo wysokiego współczynnika kompresji istnieje tylko niewielkie zmniejszenie jakości obrazu dla typowych tekstur. Należy jednak zablokować kompresję niektórych rodzajów tekstur — na przykład te, które mają znaczącą odmianę koloru w niewielkim obszarze — mogą mieć nieakceptowalne wyniki.

 Jeśli tekstury są odpowiednie dla kompresji opartej na blokach i nie potrzebują doskonałej wierności kolorów, rozważ użycie formatu skompresowanego bloku w celu zmniejszenia użycia pamięci i zużywania mniejszej przepustowości.

## <a name="remarks"></a>Uwagi
 Tekstury są kompresowane przy użyciu formatu kompresji opartego na blokach dla każdego wywołania `ID3DDevice::CreateTexture2D` , które tworzy teksturę źródłową. W szczególnych przypadkach tekstury są kompresowane, gdy:

- `D3D11_TEXTURE2D_DESC`Obiekt przeszedł w programie `pDesc` opisuje zmianę zasobu programu do cieniowania, czyli:

  - Element członkowski BindFlags ma tylko ustawioną flagę D3D11_BIND_SHADER_RESOURCE.

  - Element członkowski użycia ma ustawioną wartość D3D11_USAGE_DEFAULT lub D3D11_USAGE_IMMUTABLE.

  - Element członkowski CPUAccessFlags ma wartość 0 (brak dostępu procesora).

  - Element członkowski SamplerDesc ma ustawioną wartość 1 (bez wygładzania).

- Początkowe dane są dostarczane do wywołania `CreateTexture2D` .

  Oto obsługiwane formaty źródłowe i ich formaty skompresowane w bloku.

|Oryginalny format (od)|Format skompresowany (do)|
|------------------------------|------------------------------|
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (dawniej DXT1)|
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (dawniej DXT5)|
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|

 Jeśli tekstura ma format, którego nie ma na liście, tekstura nie jest modyfikowana.

## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia
 Czasami tekstury, które są tworzone z odmianą formatu obrazu B8G8R8A8 lub R8G8B8A8, nie używają kanału alfa, ale nie ma żadnego sposobu, aby określić, czy jest on używany, czy nie. Aby zachować poprawność na wypadek użycia kanału alfa, wariant zawsze koduje te formaty w formacie mniej wydajnym BC3. Możesz pomóc analiza klatek grafiki lepiej zrozumieć potencjalną wydajność renderowania aplikacji za pomocą tego wariantu przy użyciu odmiany formatu obrazu B8G8R8X8, gdy nie używasz kanału alfa, aby wariant mógł używać bardziej wydajnego formatu BC1.

## <a name="example"></a>Przykład
 Ten blok wariantu — kompresuje tekstury w czasie wykonywania przed wywołaniem do `CreateTexture2D` . Zalecamy stosowanie tego podejścia do kodu produkcyjnego, ponieważ nieskompresowane tekstury zużywają więcej miejsca na dysku, ponieważ dodatkowy krok może znacząco zwiększyć czas ładowania w aplikacji, ponieważ kompresja oparta na blokach wymaga znaczących zasobów obliczeniowych. Zamiast tego zalecamy kompresję tekstury w trybie offline przy użyciu edytora obrazu lub procesora obrazu, który jest częścią potoku kompilacji. Metody te zmniejszają wymagania dotyczące miejsca na dysku, eliminują obciążenia w czasie wykonywania w aplikacji i zapewniają większy czas przetwarzania, aby zachować najlepszą jakość obrazu.

## <a name="see-also"></a>Zobacz też
- [Wariant wymiarów tekstury połówkowej/Kwartałowej](half-quarter-texture-dimensions-variant.md)