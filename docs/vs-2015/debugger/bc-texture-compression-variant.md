---
title: Wariant kompresji tekstury BC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 818998511a4ef8b7f10b8225e71b414edafd9769
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736561"
---
# <a name="bc-texture-compression-variant"></a>Wariant kompresji tekstury BC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Umożliwia zablokowanie kompresji tekstury, które mają format pikseli, który jest odmianą B8G8R8X8, B8G8R8A8 lub R8G8B8A8.  
  
## <a name="interpretation"></a>Interpretacja  
 Formatów kompresji opartej na blokach, takich jak BC1, BC2, i BC3 zajmować znacznie mniej pamięci niż nieskompresowany formatów obrazów i w związku z tym zużywać znacznie mniej przepustowości pamięci. W porównaniu do nieskompresowanych formatu, który używa 32 bity na piksel (wcześniej znane jako DXT1) BC1 osiąga kompresji 8:1 i BC3 (wcześniej znane jako DXT5) zwiększona 4:1. Różnica między BC1 i BC3 jest BC1 nie obsługuje kanał alfa, natomiast BC3 obsługuje skompresowanego bloku kanału alfa. Pomimo współczynniki wysoką kompresję istnieje tylko drobne obniżenie jakości obrazu dla typowych tekstury. Jednak block kompresji niektórych rodzajów tekstury — na przykład tych, które mają znaczący kolor zmienność mały obszar — może mieć można zaakceptować wyniki.  
  
 Jeśli Twoje tekstury są odpowiednie na potrzeby kompresji opartej na blokach i nie potrzebujesz doskonała koloru, należy wziąć pod uwagę przy użyciu formatu skompresowanego bloku zmniejszenie zużycia pamięci i używanie mniejszej przepustowości.  
  
## <a name="remarks"></a>Uwagi  
 Można kompresować tekstury, używając formatu kompresji opartej na blokach na każde wywołanie `ID3DDevice::CreateTexture2D` tworząca źródłową teksturę. W szczególności tekstury są kompresowane, gdy:  
  
- `D3D11_TEXTURE2D_DESC` Obiekt przekazany w `pDesc` opisuje niezmiennych zasób programu do cieniowania; będącego:  
  
  -   Element członkowski BindFlags ma tylko D3D11_BIND_SHADER_RESOURCE ustawiona jest flaga.  
  
  -   Użycie elementu członkowskiego jest równa D3D11_USAGE_DEFAULT lub D3D11_USAGE_IMMUTABLE.  
  
  -   Element członkowski CPUAccessFlags jest równa 0 (Brak dostępu Procesora).  
  
  -   Element członkowski SamplerDesc ma członków liczba równa 1 (nie próbkowanie Wygładzanie (MSAA)).  
  
- Początkowe dane są dostarczane do wywołania `CreateTexture2D`.  
  
  Poniżej przedstawiono formaty obsługiwanego źródła i ich formatów skompresowanego bloku.  
  
|Oryginalnym formacie (od)|Format skompresowany (do)|  
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
  
 Jeśli Twoje tekstury formatu, który nie ma na liście, Tekstura nie jest modyfikowany.  
  
## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia  
 Czasami tekstury, które zostały utworzone z odmianą formatów obrazów B8G8R8A8 lub R8G8B8A8 faktycznie nie używaj kanał alfa, ale nie ma możliwości dla wariantu dowiedzieć się, czy jest używana w czy nie. Aby zapewnić poprawność, w przypadku, gdy jest używany kanał alfa, wariant zawsze koduje te formaty w mniej efektywnego format BC3. Możesz pomóc lepiej zrozumieć aplikacji granicę potencjalnej wydajności renderowania z wariantu przy użyciu odmianą B8G8R8X8 format obrazu, jeśli nie używasz kanał alfa, dzięki czemu wariant można użyć bardziej wydajne formatu BC1 analiza klatek grafiki.  
  
## <a name="example"></a>Przykład  
 Ten wariant bloku kompresuje tekstury w czasie wykonywania, przed wywołaniem do `CreateTexture2D`. Zalecamy takie podejście dla kodu produkcyjnego, ponieważ bez kompresji tekstury zużywać więcej miejsca na dysku i dodatkowego kroku może znacznie zwiększyć czas ładowania w swojej aplikacji, ponieważ kompresji opartej na blokach wymaga znaczących zasoby obliczeniowe do zakodowania. Zamiast tego zaleca się, można kompresować tekstury w trybie offline przy użyciu edytora obrazów lub procesor obrazów, który jest częścią potoku kompilacji. Te metody zmniejszyć wymagania dotyczące miejsca na dysku, wyeliminować środowiska wykonawczego obciążenie w swojej aplikacji i dają więcej czasu na przetwarzanie tak, aby zachować najlepszej jakości obrazu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wariant wymiarów jednej ósmej tekstury](../debugger/half-quarter-texture-dimensions-variant.md)



