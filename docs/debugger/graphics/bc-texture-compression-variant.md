---
title: Wariant kompresji tekstury BC | Microsoft Docs
description: Użyj wariantu kompresji tekstury BC, aby zezwolić na kompresję bloków (BC) dla tekstur o formacie pikseli, który jest odmianą formatu B8G8R8X8, B8G8R8A8 lub R8G8B8A8.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1a8699980599a590b6f6e58e14ea504f52db609
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232755"
---
# <a name="bc-texture-compression-variant"></a>Wariant kompresji tekstury BC
Włącza kompresję bloków tekstur o formacie pikseli, który jest odmianą B8G8R8X8, B8G8R8A8 lub R8G8B8A8.

## <a name="interpretation"></a>Interpretacja
 Formaty kompresji blokowej, takie jak BC1, BC2 i BC3, zajmują znacznie mniej pamięci niż formaty nieskompresowanych obrazów i w związku z tym zużywają znacznie mniej przepustowości pamięci. W porównaniu do nieskompresowanych formatów, które wykorzystują 32 bity na piksel, BC1 (wcześniej znany jako DXT1) osiąga kompresję 8:1, a BC3 (wcześniej znany jako DXT5) osiąga wartość 4:1. Różnica między BC1 i BC3 polega na tym, że BC1 nie obsługuje kanału alfa, podczas gdy BC3 obsługuje kanał alfa skompresowany blokowo. Pomimo wysokiego współczynnika kompresji istnieje tylko niewielka redukcja jakości obrazu dla typowych tekstur. Jednak blokowanie kompresji niektórych rodzajów tekstur — na przykład tych, które mają znaczące zmiany kolorów w małym obszarze — może mieć nieakceptowalne wyniki.

 Jeśli tekstury są odpowiednie do kompresji opartej na blokach i nie wymagają idealnej wierności kolorów, rozważ użycie formatu skompresowanego blokowo, aby zmniejszyć użycie pamięci i zmniejszyć wykorzystanie przepustowości.

## <a name="remarks"></a>Uwagi
 Kompresuje się tekstury przy użyciu formatu kompresji opartej na blokach przy każdym wywołaniu funkcji , która `ID3DDevice::CreateTexture2D` tworzy teksturę źródłową. W szczególności tekstury są kompresowane, gdy:

- Przekazany `D3D11_TEXTURE2D_DESC` obiekt opisuje `pDesc` niezmieniony zasób modułu cieniującego, czyli:

  - Członek BindFlags ma tylko D3D11_BIND_SHADER_RESOURCE flagę.

  - Dla członka Użycie ustawiono wartość D3D11_USAGE_DEFAULT lub D3D11_USAGE_IMMUTABLE.

  - CpuAccessFlags jest ustawiona na 0 (bez dostępu do procesora CPU).

  - Członek SamplerDesc ma swój członek Count ustawiony na 1 (brak wielo sample anti-aliasing (MSAA)).

- Początkowe dane są przekazywane do wywołania `CreateTexture2D` .

  Poniżej znajdują się obsługiwane formaty źródeł i ich formaty skompresowane blokowo.

|Oryginalny format (od)|Skompresowany format (do)|
|------------------------------|------------------------------|
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (dawniej DXT1)|
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|Bc1|
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|Bc1|
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (dawniej DXT5)|
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|

 Jeśli tekstura ma format, który nie jest wymieniony, tekstura nie jest modyfikowana.

## <a name="restrictions-and-limitations"></a>Ograniczenia
 Czasami tekstury tworzone przy użyciu odmian formatów obrazów B8G8R8A8 lub R8G8B8A8 w rzeczywistości nie używają kanału alfa, ale nie ma możliwości, aby wariant wiedział, czy jest używany. Aby zachować poprawność w przypadku użycia kanału alfa, wariant zawsze koduje te formaty do mniej wydajnego formatu BC3. Ten wariant analiza klatek grafiki lepiej zrozumieć potencjalną wydajność renderowania aplikacji, używając wariantu formatu obrazu B8G8R8X8, gdy nie jest używany kanał alfa, dzięki czemu wariant może korzystać z bardziej wydajnego formatu BC1.

## <a name="example"></a>Przykład
 Ten wariant bloku kompresuje tekstury w czasie uruchamiania, przed `CreateTexture2D` wywołaniem . Zalecamy takie podejście w przypadku kodu produkcyjnego, ponieważ nieskompresowane tekstury zużywają więcej miejsca na dysku i ponieważ dodatkowy krok może znacznie zwiększyć czas ładowania w aplikacji, ponieważ kompresja oparta na blokach wymaga znaczących zasobów obliczeniowych do kodowania. Zamiast tego zalecamy kompresowanie tekstur w trybie offline przy użyciu edytora obrazów lub procesora obrazów, który jest częścią potoku kompilacji. Te podejścia zmniejszają wymagania dotyczące miejsca na dysku, eliminują obciążenie w czasie działania w aplikacji i skracają czas przetwarzania, dzięki czemu można zachować najlepszą jakość obrazu.

## <a name="see-also"></a>Zobacz też
- [Wariant wymiarów połowy/ćwiartki tekstury](half-quarter-texture-dimensions-variant.md)