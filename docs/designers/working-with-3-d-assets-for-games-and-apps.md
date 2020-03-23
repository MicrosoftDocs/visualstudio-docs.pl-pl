---
title: Praca z zasobami 3D dla gier i aplikacji
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa9fc04df3e817730492353e54d74c1e46c3775e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589802"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Praca z zasobami 3D dla gier i aplikacji

W tym artykule opisano narzędzia programu Visual Studio, których można używać do tworzenia lub modyfikowania modeli 3D, tekstur i modułów cieniujących dla gier i aplikacji opartych na technologii DirectX.

## <a name="directx-app-development-in-visual-studio"></a>Tworzenie aplikacji DirectX w programie Visual Studio

Aplikacja DirectX zazwyczaj łączy logikę programowania, interfejs API DirectX i programy języka cieniowania wysokiego poziomu (HLSL), a także zasoby audio i wizualne 3D, aby zaprezentować bogate, interaktywne środowisko multimedialne. Program Visual Studio zawiera narzędzia, których można używać do pracy z obrazami i teksturami, modelami 3D i modułami cieniujących bez pozostawiania IDE do użycia innego narzędzia. Narzędzia programu Visual Studio są szczególnie odpowiednie do tworzenia zasobów *zastępczych,* których można użyć do testowania kodu lub tworzenia prototypów przed uruchomieniem zasobów gotowych do produkcji oraz do sprawdzania i modyfikowania zasobów gotowych do produkcji podczas debugowania aplikacji.

Oto więcej informacji na temat rodzajów zasobów, z którymi można pracować w programie Visual Studio.

### <a name="images-and-textures"></a>Obrazy i tekstury

Obrazy i tekstury zapewniają kolor i szczegóły wizualne w grach i aplikacjach. W grafice 3D tekstury są dostępne w różnych formatach, typach i geometriach, aby obsługiwać różne zastosowania. Na przykład normalne mapy zapewniają normals powierzchni na piksel dla bardziej szczegółowego oświetlenia modeli 3D, a mapy sześcianów zapewniają teksturę we wszystkich kierunkach do zastosowań, takich jak sky-boxing, odbicia i mapowanie tekstur sferycznych. Tekstury mogą zapewniać mipmaps do obsługi wydajnego renderowania na różnych poziomach szczegółowości i mogą obsługiwać różne kanały kolorów i kolejności kolorów. Tekstury mogą być przechowywane w różnych formatach skompresowanych, które zajmują mniej dedykowanej pamięci graficznej i pomagają procesorom GPU uzyskać bardziej wydajny dostęp do tekstur.

Edytor obrazów programu Visual Studio służy do pracy z obrazami i teksturami w wielu typowych typach i formatach.

### <a name="3d-models"></a>Modele 3D

Modele 3D tworzą przestrzeń i kształt w grach i aplikacjach. Minimalnie modele kodują położenie punktów w przestrzeni 3D , które są znane jako *wierzchołki*, wraz z danymi indeksowania w celu zdefiniowania linii lub trójkątów, które reprezentują kształt modelu. Z tymi wierzchołkami można skojarzyć dodatkowe dane — na przykład informacje o kolorze, normalne wektory lub atrybuty specyficzne dla aplikacji. Każdy model może również definiować atrybuty dla całego obiektu , na przykład, który moduł cieniujący jest używany do obliczania wyglądu powierzchni obiektu lub która tekstura jest do niego stosowana.

Edytora modeli programu Visual Studio można używać do pracy z modelami 3D w kilku typowych formatach.

### <a name="shaders"></a>Programy do cieniowania

Moduły cieniowania to małe programy specyficzne dla domeny, które działają na procesorze graficznym (GPU). Moduły cieniowania określają sposób przekształcania modeli 3D w kształty ekranowe i sposób kolorowania każdego piksela w tych kształtach. Tworząc moduł cieniujący i stosując go do obiektu w grze lub aplikacji, można nadać obiektowi niepowtarzalny wygląd.

Projektant modułu cieniującego programu Visual Studio, który jest narzędziem do projektowania modułów cieniowania opartych na wykresie, służy do tworzenia niestandardowych efektów wizualnych bez znajomości programowania HLSL.

> [!NOTE]
> Aby uzyskać więcej informacji na temat uruchamiania programowania DirectX, zobacz [DirectX](/windows/win32/directx). Aby uzyskać więcej informacji na temat debugowania aplikacji opartej na technologii DirectX, zobacz [Diagnostyka grafiki (debugowanie grafiki DirectX).](../debugger/graphics/visual-studio-graphics-diagnostics.md)

## <a name="directx-version-compatibility"></a>Zgodność wersji programu DirectX

Visual Studio używa directx do renderowania zasobów 2D i 3D. Można wybrać moduł renderowania DirectX 11 lub moduł renderowania oprogramowania WARP (Advanced Rasterization Platform) systemu Windows. Renderer DirectX 11 zapewnia wydajne, przyspieszane sprzętowo renderowanie na procesorach graficznych DirectX 11 i DirectX 10. Moduł renderowania WARP pomaga upewnić się, że zasoby działają z szeroką gamą komputerów — dotyczy to również komputerów, które nie mają nowoczesnego sprzętu graficznego i komputerów ze zintegrowanym sprzętem graficznym. Aby uzyskać więcej informacji na temat warp, zobacz [Windows Advanced Rasterization Platform (WARP) przewodnik](/windows/win32/direct3darticles/directx-warp).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z teksturami i obrazami](../designers/working-with-textures-and-images.md)|W tym artykule opisano, jak używać programu Visual Studio do pracy z obrazami i teksturami.|
|[Praca z modelami 3D](../designers/working-with-3-d-models.md)|W tym artykule opisano sposób korzystania z programu Visual Studio do pracy z modelami 3D.|
|[Praca z modułami cieniu w cieniu](../designers/working-with-shaders.md)|W tym artykule opisano sposób tworzenia i modyfikowania niestandardowych efektów modułu cieniującego za pomocą projektanta modułu cieniującego programu Visual Studio.|
|[Korzystanie z zasobów 3D w grze lub aplikacji](../designers/using-3-d-assets-in-your-game-or-app.md)|W tym artykule opisano sposób używania zasobów utworzonych za pomocą Edytora obrazów, Edytora modeli lub Projektanta modułów cieniucych w grze lub aplikacji.|
