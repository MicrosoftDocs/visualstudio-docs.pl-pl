---
title: Wariant wymiarów tekstury półrocza | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4c82836f5a80fae421a30721d8c3ee4c3d6893d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735393"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Wariant wymiarów połowy/ćwiartki tekstury
Zmniejsza wymiary tekstury dla tekstury, które nie są obiektami docelowymi.

## <a name="interpretation"></a>Błędne
 Mniejsze tekstury zajmują mniej pamięci i w związku z tym zużywają mniejszą przepustowość pamięci i zmniejszają nacisk na pamięć podręczną tekstury procesora GPU. Jednak ich mniejsze szczegóły mogą spowodować zmniejszenie jakości obrazu, zwłaszcza wtedy, gdy są one widoczne blisko sceny trójwymiarowych lub wyświetlane w obszarze powiększenia.

 Jeśli ten wariant pokazuje duży wzrost wydajności, może to wskazywać, że aplikacja zużywa zbyt dużą przepustowość pamięci, używa niewydajnej pamięci podręcznej tekstury lub obu tych metod. Może również wskazywać, że tekstury zajmują większą ilość pamięci GPU niż dostępna, co powoduje, że tekstury są stronicowane do pamięci systemowej.

 Jeśli aplikacja zużywa zbyt dużo pamięci lub używa niewydajnej pamięci podręcznej tekstury, należy rozważyć zmniejszenie rozmiaru tekstury, ale tylko po włączeniu funkcji mapy MIP dla odpowiednich tekstur. Podobnie jak w przypadku mniejszych tekstur, tekstury mapowane przez MCI zużywają mniejszą przepustowość pamięci, chociaż zajmują więcej pamięci GPU i zwiększają wykorzystanie pamięci podręcznej, ale nie redukują szczegółów tekstury. Zaleca się, aby w każdym przypadku zwiększone użycie pamięci nie powodowało, aby tekstury były stronicowane do pamięci systemowej.

 Jeśli tekstury zajmują większą ilość pamięci GPU niż jest dostępna, należy rozważyć zmniejszenie rozmiaru tekstury, ale dopiero po rozważeniu kompresji odpowiednich tekstur. Podobnie jak w przypadku mniejszych tekstur, skompresowane tekstury zajmują mniej pamięci i zmniejszają potrzebę przenoszące się do pamięci systemowej, ale ich wierność kolorów są ograniczone. Kompresja nie jest odpowiednia dla wszystkich tekstur, w zależności od ich zawartości — na przykład te, które mają znaczącą odmianę koloru w niewielkim obszarze — ale w przypadku wielu tekstur kompresja może zachować lepszą ogólną jakość obrazu niż zmniejszenie ich rozmiaru.

## <a name="remarks"></a>Uwagi
 Wymiary tekstury są redukowane dla każdego wywołania `ID3D11Device::CreateTexture2D`, które tworzy teksturę źródłową. W odróżnieniu od tego, czy wymiary tekstury są ograniczone, gdy obiekt D3D11_TEXTURE2D_DESC przeszedł w `pDesc` opisuje teksturę używaną podczas renderowania; Czyli:

- Element członkowski BindFlags ma tylko ustawioną flagę D3D11_BIND_SHADER_RESOURCE.

- Element członkowski MiscFlags nie ma flagi D3D11_RESOURCE_MISC_TILE_POOL lub ustawionej flagi D3D11_RESOURCE_MISC_TILED (rozłączone zasoby nie są zmieniane).

- Format tekstury jest obsługiwany jako obiekt docelowy renderowania — określony przez D3D11_FORMAT_SUPPORT_RENDER_TARGET — który jest wymagany do zmniejszenia rozmiaru tekstury. Formaty BC1, BC2 i BC3 są również obsługiwane, mimo że nie są obsługiwane jako elementy docelowe renderowania.

  Jeśli dane początkowe są dostarczane przez aplikację, ten wariant skaluje dane tekstury do odpowiedniego rozmiaru przed utworzeniem tekstury. Jeśli dane początkowe są dostarczane w formacie skompresowanym bloku, takim jak BC1, BC2 lub BC3, jest dekodowane, skalowane i ponownie kodowane przed użyciem do utworzenia mniejszej tekstury. (Charakter kompresji opartej na blokach oznacza, że proces dodatkowego kodowania skalowania w poziomie prawie zawsze powoduje obniżenie jakości obrazu, niż w przypadku generowania tekstury skompresowanej bloków z skalowanej wersji tekstury, która nie była wcześniej zakodowana).

  Jeśli dla tekstury włączone są mapy MIP, wariant zmniejszy odpowiednio liczbę poziomów MIP, co jest mniejsze w przypadku skalowania na połowę lub dwa mniejsze skalowanie do rozmiaru kwartału.

## <a name="example"></a>Przykład
 Ten wariant zmienia rozmiar tekstury w czasie wykonywania przed wywołaniem do `CreateTexture2D`. Zalecamy stosowanie tego podejścia do kodu produkcyjnego, ponieważ tekstury o pełnym rozmiarze zużywają więcej miejsca na dysku, ponieważ dodatkowy krok może zwiększyć czas ładowania w aplikacji — szczególnie w przypadku skompresowanych tekstur, które wymagają znaczącego obliczenia zasoby do zakodowania. Zamiast tego zalecamy zmianę rozmiaru tekstury w tryb offline przy użyciu edytora obrazu lub procesora obrazu, który jest częścią potoku kompilacji. Te podejścia zmniejszają wymagania dotyczące miejsca na dysku i eliminują obciążenie środowiska uruchomieniowego w aplikacji oraz zapewniają większy czas przetwarzania, dzięki czemu można zachować najlepszą jakość obrazu podczas zmniejszania lub kompresowania tekstur.

## <a name="see-also"></a>Zobacz także
- [Wariant generowania mipmapy](mip-map-generation-variant.md)
- [Wariant kompresji tekstury BC](bc-texture-compression-variant.md)