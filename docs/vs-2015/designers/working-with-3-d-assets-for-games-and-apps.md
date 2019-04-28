---
title: Praca z obiektami 3-d do gier i aplikacji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 020c934d3427dda77c41fb410143972d6f48656b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438097"
---
# <a name="working-with-3-d-assets-for-games-and-apps"></a>Praca z obiektami 3-D do gier i aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie opisano [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi służących do tworzenia lub modyfikowania modeli 3D, tekstury i programów do cieniowania dla aplikacji i gier w technologii DirectX.  
  
## <a name="directx-app-development-in-visual-studio"></a>Rozwoju aplikacji DirectX w programie Visual Studio  
 Aplikacja DirectX zazwyczaj łączy logikę programistyczną, interfejsu API programu DirectX i programów High Level cieniowanie Language (HLSL), wraz z audio i 3-wizualnych elementów zawartości do przedstawienia bogate, interaktywne środowisko multimedialnych.[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zawiera narzędzia, które służą do pracy z obrazów i tekstur, modele 3D i programów do cieniowania bez opuszczania środowiska IDE, aby użyć innego narzędzia. Narzędzia programu Visual Studio są szczególnie nadaje się do tworzenia *symbolu zastępczego* zasoby, których można użyć do testowania kodu lub twórz prototypy, przed Komisji zasobów gotowych do produkcji i do inspekcji i modyfikacji gotowe do produkcji zasoby podczas debugowania aplikacji.  
  
 Poniżej przedstawiono więcej informacji na temat rodzajów zasobów, które można pracować w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="images-and-textures"></a>Obrazów i tekstur  
 Obrazów i tekstur, zapewniają koloru i wizualne szczegółowo gier i aplikacji. W grafika 3-D tekstury są dostępne w różnych formatach, typy i geometrii obsługuje różne sposoby zastosowania. Na przykład map normalnych zapewnienia bardziej szczegółowy oświetlenia z modelami 3-D normalne powierzchni każdego piksela i cubemaps zapewniają tekstury na wszystkie kierunki do celów takich jak sky opakowywania odbić i mapowanie kulistego tekstury. Tekstury może zapewnić mapy mip umożliwiających wydajne renderowanie na różnych poziomach szczegółowości i może obsługiwać różnych kanałów i uporządkowania kolorów. Tekstury mogą być przechowywane w różnych formatach skompresowany, zajmują mniej dedykowanego grafiki pamięci i procesorów GPU dostęp do tekstury wydajniej.  
  
 Możesz użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora obrazów, aby pracować z obrazów i tekstur w wielu typowych typów i formatów.  
  
### <a name="3-d-models"></a>modele 3-D  
 Modele 3-D Utwórz miejsce i kształt w grach i aplikacjach. Co najmniej modeli kodowanie położenie punktów w przestrzeni 3D — które są znane jako *wierzchołki*— wraz z indeksować dane w celu definiowania linie lub trójkąty, które reprezentują kształt modelu. Dodatkowe dane mogą być skojarzone z tymi wierzchołkami — na przykład koloru informacje, normalne wektorów lub atrybuty specyficzne dla aplikacji. Każdy model można również zdefiniować atrybuty na poziomie obiektu — na przykład, który program do cieniowania jest używana do obliczania wygląd obiektu powierzchni, lub tekstury, które są stosowane do niego.  
  
 Możesz użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora modelu do pracy z 3-w modelach w kilku typowych formatach.  
  
### <a name="shaders"></a>Programy do cieniowania  
 Programy do cieniowania są małe, specyficznego dla domeny programów, które działają na jednostka przetwarzania grafiki (GPU). Modele 3-D jak ustalić, programów do cieniowania są przekształcane na ekranie kształtów i jak jest kolor każdego piksela te kształty. Tworzenie modułu cieniującego i zastosowanie go do obiektu w grach i aplikacjach, można przekazać obiekt unikatowego wyglądu.  
  
 Możesz użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektanta cieniowania, który jest narzędzie do projektowania na podstawie wykresu programu do cieniowania, tworzenie niestandardowych efektów wizualnych bez znajomości języka HLSL programowania.  
  
> [!NOTE]
> Aby uzyskać więcej informacji dotyczących sposobu uruchamiania z programowaniem DirectX, zobacz [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633). Aby uzyskać więcej informacji na temat debugowania aplikacji opartych na technologii DirectX, zobacz [Graphics Diagnostics (debugowanie grafiki DirectX)](../debugger/visual-studio-graphics-diagnostics.md).  
  
## <a name="directx-version-compatibility"></a>Zgodność wersji programu DirectX  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używa programu DirectX do renderowania zasobów 2W i 3W. Możesz wybrać renderowania programu DirectX 11 lub renderowanie programowe Windows Advanced rasteryzacji platformy WARP (). Moduł renderowania programu DirectX 11 zawiera renderowania o wysokiej wydajności, przyspieszanych sprzętowo programu DirectX 11 i technologii DirectX 10 GPU. Moduł renderowania WARP pomaga upewnić się, że Twoje zasoby współdziałać z szerokiej gamy komputerów — obejmuje to komputery, których nie zainstalowano sprzęt graficzny nowoczesnych i komputerów, które mają zintegrowany sprzętu graficznego. Aby uzyskać więcej informacji na temat WARP, zobacz [przewodnik Windows Advanced rasteryzacji platformy WARP ()](http://go.microsoft.com/fwlink/p/?LinkId=224634).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Praca z obrazami i teksturami](../designers/working-with-textures-and-images.md)|Opisuje sposób używania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do pracy z obrazów i tekstur.|  
|[Praca z modelami 3-D](../designers/working-with-3-d-models.md)|Opisuje sposób używania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do pracy z modelami 3-D.|  
|[Praca z cieniowaniem](../designers/working-with-shaders.md)|Opisuje sposób używania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Shader Designer do tworzenia i modyfikowania efekty cieniowania niestandardowych.|  
|[Korzystanie z obiektów 3-D w grach i aplikacjach](../designers/using-3-d-assets-in-your-game-or-app.md)|W tym artykule opisano sposób użycia zasobów, które utworzono przy użyciu edytora obrazów, edytora modeli lub projektanta modułu cieniującego w grach i aplikacjach.|
