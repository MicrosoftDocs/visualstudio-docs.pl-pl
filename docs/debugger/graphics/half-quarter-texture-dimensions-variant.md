---
title: Half-Quarter wymiarów tekstury | Microsoft Docs
description: Jeśli mniejsze tekstury wskazują na duży wzrost wydajności, sugeruje wykorzystanie przepustowości pamięci lub niewydajne użycie pamięci podręcznej tekstur procesora GPU. Rozważ mniejsze rozmiary tekstur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ddd446e588af438e1a4d950e9407392e74881f90
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232404"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Wariant wymiarów połowy/ćwiartki tekstury
Zmniejsza wymiary tekstury na teksturach, które nie są celami renderowania.

## <a name="interpretation"></a>Interpretacja
 Mniejsze tekstury zajmują mniej pamięci i w związku z tym zużywają mniej przepustowości pamięci i zmniejszają obciążenie pamięci podręcznej tekstur procesora GPU. Jednak ich mniejsza szczegółowość może spowodować obniżenie jakości obrazu, szczególnie gdy są one ściśle oglądane w scenie 3D lub przeglądane przy powiększeniu.

 Jeśli ten wariant pokazuje duży wzrost wydajności, może to wskazywać, że aplikacja zużywa zbyt dużą przepustowość pamięci, nieefektywnie używa pamięci podręcznej tekstur lub obu tych programów. Może również wskazywać, że tekstury zajmują więcej pamięci procesora GPU niż jest dostępna, co powoduje stronicowanie tekstur w pamięci systemowej.

 Jeśli aplikacja zużywa zbyt dużo pamięci lub nieefektywnie używa pamięci podręcznej tekstur, rozważ zmniejszenie rozmiaru tekstur, ale dopiero po rozważeniu włączenia mip-maps dla odpowiednich tekstur. Podobnie jak mniejsze tekstury, tekstury mapowane przez mip zużywają mniej przepustowości pamięci — chociaż zajmują więcej pamięci procesora GPU — i zwiększają wykorzystanie pamięci podręcznej, ale nie zmniejszają szczegółów tekstury. Zalecamy mip-maps za każdym razem, gdy zwiększone użycie pamięci nie powoduje stronicowania tekstur w pamięci systemowej.

 Jeśli tekstury zajmują więcej pamięci procesora GPU niż jest dostępna, rozważ zmniejszenie rozmiaru tekstur, ale dopiero po rozważeniu skompresowania odpowiednich tekstur. Podobnie jak mniejsze tekstury, skompresowane tekstury zajmują mniej pamięci i zmniejszają potrzebę stronicowania do pamięci systemowej, ale ich wierność kolorów jest mniejsza. Kompresja nie jest odpowiednia dla wszystkich tekstur, w zależności od ich zawartości — na przykład tych, które mają znaczące zmiany kolorów w małym obszarze — ale w przypadku wielu tekstur kompresja może zachować lepszą ogólną jakość obrazu niż zmniejszenie ich rozmiaru.

## <a name="remarks"></a>Uwagi
 Wymiary tekstury są zmniejszane przy każdym wywołaniu do `ID3D11Device::CreateTexture2D` , które tworzy teksturę źródłową. W szczególności wymiary tekstury są zmniejszane, D3D11_TEXTURE2D_DESC przekazany obiekt opisuje teksturę używaną `pDesc` podczas renderowania, czyli:

- Członek BindFlags ma tylko D3D11_BIND_SHADER_RESOURCE flagi.

- Członek MiscFlags nie ma flagi D3D11_RESOURCE_MISC_TILE_POOL ani D3D11_RESOURCE_MISC_TILED flagi (rozmiar kafelków zasobów nie jest zmieniany).

- Format tekstury jest obsługiwany jako cel renderowania — określony przez D3D11_FORMAT_SUPPORT_RENDER_TARGET — co jest wymagane do zmniejszenia rozmiaru tekstury. Obsługiwane są również formaty BC1, BC2 i BC3, mimo że nie są obsługiwane jako obiekty docelowe renderowania.

  Jeśli dane początkowe są dostarczane przez aplikację, ten wariant skaluje dane tekstury do odpowiedniego rozmiaru przed utworzeniem tekstury. Jeśli dane początkowe są dostarczane w formacie skompresowanym blokowo, takim jak BC1, BC2 lub BC3, są dekodowane, skalowane i ponownie kodowane przed utworzeniem mniejszej tekstury. (Charakter kompresji opartej na blokach oznacza, że dodatkowy proces kodowania w skali dekodowania prawie zawsze powoduje niższą jakość obrazu niż w przypadku wygenerowania tekstury skompresowanej blokowo na podstawie skalowanej wersji tekstury, która nie została wcześniej zakodowana).

  Jeśli mapy mip są włączone dla tekstury, wariant odpowiednio zmniejsza liczbę poziomów mip — o jeden mniej podczas skalowania do połowy rozmiaru lub o dwa mniej podczas skalowania do rozmiaru ćwiartki.

## <a name="example"></a>Przykład
 Ten wariant zmienia rozmiar tekstur w czasie uruchamiania przed wywołaniem `CreateTexture2D` . Zalecamy stosowanie tego podejścia w przypadku kodu produkcyjnego, ponieważ tekstury w pełnym rozmiarze zużywają więcej miejsca na dysku i ponieważ dodatkowy krok może zwiększyć czas ładowania w aplikacji — szczególnie w przypadku skompresowanych tekstur, które wymagają kodowania znaczących zasobów obliczeniowych. Zamiast tego zalecamy zmianę rozmiaru tekstur w trybie offline przy użyciu edytora obrazów lub procesora obrazów, który jest częścią potoku kompilacji. Te podejścia zmniejszają wymagania dotyczące miejsca na dysku i eliminują obciążenie środowiska uruchomieniowego w aplikacji oraz skracają czas przetwarzania, dzięki czemu można zachować najlepszą jakość obrazu przy jednoczesnym zmniejszaniu lub kompresowania tekstur.

## <a name="see-also"></a>Zobacz też
- [Wariant generowania mipmapy](mip-map-generation-variant.md)
- [Wariant kompresji tekstury BC](bc-texture-compression-variant.md)