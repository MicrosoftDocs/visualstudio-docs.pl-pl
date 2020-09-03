---
title: Praca z zasobami 3W dla gier i aplikacji
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75589802"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Praca z zasobami 3D dla gier i aplikacji

W tym artykule opisano narzędzia programu Visual Studio, których można użyć do tworzenia lub modyfikowania modeli 3W, tekstur i programów do cieniowania dla gier i aplikacji opartych na technologii DirectX.

## <a name="directx-app-development-in-visual-studio"></a>Programowanie aplikacji DirectX w programie Visual Studio

Aplikacja DirectX zazwyczaj łączy logikę programistyczną, interfejs API programu DirectX i programy HLSL (High Level Cieniing Language) wraz z graficznymi zasobami audio i 3W, aby przedstawić bogate, interaktywne środowisko multimedialne. Program Visual Studio zawiera narzędzia, których można użyć do pracy z obrazami i teksturami, modelami 3W i cieniami bez opuszczania środowiska IDE do korzystania z innego narzędzia. Narzędzia programu Visual Studio są szczególnie odpowiednie do tworzenia *zastępczych* elementów zawartości, których można użyć do testowania kodu lub prototypów kompilacji przed rozpoczęciem pracy z zasobami gotowymi do produkcji oraz do inspekcji i modyfikowania zasobów gotowych do produkcji w przypadku debugowania aplikacji.

Poniżej znajduje się więcej informacji na temat rodzajów zasobów, z którymi można korzystać w programie Visual Studio.

### <a name="images-and-textures"></a>Obrazy i tekstury

Obrazy i tekstury zawierają szczegóły dotyczące kolorów i wizualizacji w grach i aplikacjach. W grafikach 3D tekstury są dostępne w różnych formatach, typach i geometrie w celu obsługi różnych celów. Na przykład normalne mapy zapewniają normalną powierzchnię dla poszczególnych pikseli na potrzeby bardziej szczegółowego oświetlenia modeli 3D, a mapy modułów zapewniają teksturę we wszystkich kierunkach, takich jak odpakowanie, odbijające i mapa tekstury sferycznej. Tekstury mogą zapewniać mipmapy do obsługi wydajnego renderowania na różnych poziomach szczegółowości i mogą obsługiwać różne kanały kolorów i kolejność kolorów. Tekstury mogą być przechowywane w różnych skompresowanych formatach, które zajmują mniej dedykowaną pamięć graficzną i są bardziej wydajne.

Możesz użyć edytora obrazów programu Visual Studio do pracy z obrazami i teksturami w wielu wspólnych typach i formatach.

### <a name="3d-models"></a>Modele 3D

modele 3W tworzą miejsce i kształt w grach i aplikacjach. Co najmniej modele zakodować pozycje punktów w przestrzeni 3D, które są znane jako *wierzchołki*— wraz z danymi indeksowania, aby definiować linie lub Trójkąty reprezentujące kształt modelu. Dodatkowe dane można kojarzyć z tymi wierzchołkami — na przykład informacje o kolorach, wektorach normalnych lub atrybuty specyficzne dla aplikacji. Każdy model może również definiować atrybuty na poziomie obiektu — na przykład, który moduł cieniujący służy do obliczenia wyglądu powierzchni obiektu lub do której jest stosowana tekstura.

Edytor modelu programu Visual Studio umożliwia korzystanie z modeli 3D w kilku wspólnych formatach.

### <a name="shaders"></a>Programy do cieniowania

Programy do cieniowania są niewielkimi programami specyficznymi dla domeny, które działają w procesorze GPU. Programy do cieniowania określają, w jaki sposób modele 3W są przekształcane na kształty na ekranie i jak kolor każdego piksela w tych kształtach. Tworząc cieniowanie i stosując je do obiektu w grze lub aplikacji, możesz nadać obiektowi unikatowy wygląd.

Możesz użyć projektanta cieniowania programu Visual Studio, który jest narzędziem do projektowania cieniowania opartym na grafie, w celu utworzenia niestandardowych efektów wizualnych bez znajomości programowania HLSL.

> [!NOTE]
> Aby uzyskać więcej informacji na temat rozpoczynania pracy z programowaniem DirectX, zobacz [DirectX](/windows/win32/directx). Aby uzyskać więcej informacji na temat debugowania aplikacji opartych na technologii DirectX, zobacz [Diagnostyka grafiki (Debugowanie grafiki DirectX)](../debugger/graphics/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>Zgodność wersji programu DirectX

Program Visual Studio używa technologii DirectX do renderowania zasobów 2D i 3W. Można wybrać moduł renderujący programu DirectX 11 lub program Windows Advanced rasteryzacji platform (Wypaczenie). Moduł renderowania DirectX 11 zapewnia wysoką wydajność, przyspieszanie sprzętowe w przypadku procesorów DirectX 11 i DirectX 10. Moduł renderowania ZNIEKSZTAŁCAnia pomaga upewnić się, że zasoby współpracują z szeroką gamą komputerów — dotyczy to również komputerów, które nie mają nowoczesnego sprzętu graficznego i komputerów z zintegrowanym sprzętem grafiki. Aby uzyskać więcej informacji na temat wypaczania, zobacz [Przewodnik dotyczący platformy Windows Advanced rasteryzacji](/windows/win32/direct3darticles/directx-warp).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z teksturami i obrazami](../designers/working-with-textures-and-images.md)|Opisuje, jak używać programu Visual Studio do pracy z obrazami i teksturami.|
|[Praca z modelami 3W](../designers/working-with-3-d-models.md)|Opisuje, jak używać programu Visual Studio do pracy z modelami 3W.|
|[Praca z cieniowaniem](../designers/working-with-shaders.md)|Opisuje, jak używać projektanta cieniowania programu Visual Studio do tworzenia i modyfikowania niestandardowych efektów cieniowania.|
|[Korzystanie z zasobów 3W w grach lub aplikacji](../designers/using-3-d-assets-in-your-game-or-app.md)|Opisuje sposób używania zasobów, które zostały utworzone przy użyciu edytora obrazów, edytora modelu lub projektanta programu do cieniowania, w grze lub aplikacji.|
