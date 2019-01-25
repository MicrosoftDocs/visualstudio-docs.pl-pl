---
title: Ósmej tekstury wymiarów wariant | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03485a3b9df9c06b1ef4755a5758cf2c8c997d1e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761089"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Wariant wymiarów tekstury połowie/kwartał
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Maksymalne wymiary tekstury na tekstury, które nie są renderowane elementów docelowych.  
  
## <a name="interpretation"></a>Interpretacja  
 Mniejsze tekstury zajmują mniej pamięci i w związku z tym zmniejszenia przepustowości przez mniej pamięci i zmniejszyć nacisk na pamięć podręczną teksturą procesora GPU. Ich szczegóły mniejszym może jednak spowodować jakości obrazu mniejsze, szczególnie w przypadku, gdy są one wyświetlane ściśle w scenie 3-D lub przeglądać w obszarze powiększenia.  
  
 Jeśli ten wariant wykazuje duże są bardziej wydajne, może to wskazywać, że aplikacja zużywa zbyt dużej ilości pamięci przepustowość i/lub nieefektywnie pamięci podręcznej tekstury używa. Można również określić, że Twoje tekstury zajmować więcej pamięci procesora GPU nie jest dostępny, co powoduje, że tekstury, które ma być stronicowana do pamięci systemowej.  
  
 Jeśli Twoja aplikacja zużywa zbyt dużej ilości pamięci przepustowość lub nieefektywnie korzysta z pamięci podręcznej tekstury, Rozważ zmniejszenie rozmiaru usługi tekstury, ale tylko wtedy, gdy należy rozważyć włączenie mapy mip dla odpowiednich tekstury. Podobnie jak tekstury mniejszych mapowane mip tekstury zmniejszenia przepustowości przez mniej pamięci — mimo że zajmują więcej pamięci procesora GPU — i wykorzystania pamięci podręcznej zwiększyć, ale nie zmniejszyć szczegółów tekstury. Firma Microsoft zaleca mapy mip, zawsze wtedy, gdy zwiększone użycie pamięci nie powoduje tekstury, które ma być stronicowana do pamięci systemowej.  
  
 Jeśli Twoje tekstury zajmują więcej pamięci procesora GPU nie jest dostępna, należy rozważyć zmniejszenie rozmiaru tekstury, ale tylko wtedy, gdy należy wziąć pod uwagę kompresji tekstury odpowiednie. Podobnie jak tekstury mniejszych skompresowany tekstury zajmują mniej pamięci i zmniejszyć do strony, aby pamięci systemowej, ale zmniejsza się ich wierności kolorów. Kompresja nie jest odpowiednia dla wszystkich tekstury, w zależności od ich zawartości — na przykład tych, które mają znaczący kolor zmienność mały obszar — przy zachowaniu dla wielu tekstury kompresji mogą lepiej ogólnej jakości obrazu niż zmniejszyć ich rozmiar.  
  
## <a name="remarks"></a>Uwagi  
 Wymiary tekstury są ograniczane na każde wywołanie `ID3D11Device::CreateTexture2D` tworząca źródłową teksturę. W szczególności wymiarów tekstury są ograniczone, gdy obiekt D3D11_TEXTURE2D_DESC przekazany w `pDesc` tekstury, które jest używane w czasie renderowania; opis:  
  
- Element członkowski BindFlags ma tylko D3D11_BIND_SHADER_RESOURCE ustawiona jest flaga.  
  
- Element członkowski MiscFlags nie ma flagi D3D11_RESOURCE_MISC_TILE_POOL lub ustawiona flaga D3D11_RESOURCE_MISC_TILED (fragmentacji zasobów nie są rozmiaru).  
  
- Format tekstury jest obsługiwany jako obiekt docelowy renderowania — zgodnie z ustaleniami D3D11_FORMAT_SUPPORT_RENDER_TARGET — co jest niezbędne do zmniejszenia rozmiaru tekstury. Formaty BC1, BC2 i BC3 również są obsługiwane, nawet jeśli nie są obsługiwane jako elementy docelowe renderowania.  
  
  Jeśli początkowe dane są dostarczane przez aplikację, ten wariant skaluje danych tekstury do odpowiedniego rozmiaru, zanim utworzy tekstury. Jeśli początkowe dane są dostarczane w formacie skompresowanego bloku, takich jak BC1, BC2 lub BC3, dekodowana, skalować i ponownie zakodowany, zanim zostaną one użyte do utworzenia mniejszych tekstury. (Rodzaj kompresji opartej na blokach oznacza, że proces bardzo dekodowania skalowania zakodować w prawie zawsze powoduje, że obniżyć jakość obrazu niż gdy tekstury skompresowanego bloku jest generowany na podstawie skalowana wersja teksturę, która nie była wcześniej zakodowany).  
  
  Włączenie mapy mip dla tekstury wariant odpowiednio zmniejsza liczbę poziomów mip — co mniej podczas skalowania w połowie lub dwóch mniejszej podczas skalowania do rozmiaru kwartału.  
  
## <a name="example"></a>Przykład  
 Ten wariant zmienia rozmiar tekstury w czasie wykonywania przed wywołaniem do `CreateTexture2D`. Zalecamy takie podejście dla kodu produkcyjnego, ponieważ pełnym wymiarze tekstury zużywać więcej miejsca na dysku i dodatkowego kroku może zwiększyć czas ładowania w swojej aplikacji — zwłaszcza w przypadku skompresowanych tekstury, które wymagają znaczących obliczeniową zasoby do zakodowania. Zamiast tego zaleca się rozmiar tekstury w trybie offline przy użyciu edytora obrazów lub procesor obrazów, który jest częścią potoku kompilacji. Tych metod zmniejszyć wymagania dotyczące miejsca na dysku i wyeliminować koszty środowiska uruchomieniowego w aplikacji i zapewniają więcej czasu na przetwarzanie tak, aby można zachować najlepszej jakości obrazu podczas zmniejszania lub kompresowanie swoje tekstury.  
  
## <a name="see-also"></a>Zobacz też  
 [Wariant generowania mipmapy](../debugger/mip-map-generation-variant.md)   
 [Wariant kompresji tekstury BC](../debugger/bc-texture-compression-variant.md)
