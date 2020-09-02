---
title: Praca z zasobami 3-D w grach i aplikacjach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e181500beefd32dffb9c0e8a7572a198cc9ff1f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852195"
---
# <a name="working-with-3-d-assets-for-games-and-apps"></a>Praca z obiektami 3-D do gier i aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie opisano [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Narzędzia, których można użyć do tworzenia lub modyfikowania modeli trójwymiarowych, tekstur i programów do cieniowania dla gier i aplikacji opartych na technologii DirectX.

## <a name="directx-app-development-in-visual-studio"></a>Programowanie aplikacji DirectX w programie Visual Studio
 Aplikacja DirectX zazwyczaj łączy logikę programowania, interfejs API programu DirectX i programy HLSL (High Level Cieniing Language) wraz z dźwiękiem i 3-D zasobami wizualnymi w celu zaprezentowania rozbudowanego, interaktywnego środowiska multimedialnego.[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obejmuje narzędzia, których można użyć do pracy z obrazami i teksturami, modelami 3-D i cieniami bez opuszczania środowiska IDE do korzystania z innego narzędzia. Narzędzia programu Visual Studio są szczególnie odpowiednie do tworzenia *zastępczych* elementów zawartości, których można użyć do testowania kodu lub prototypów kompilacji przed rozpoczęciem pracy z zasobami gotowymi do produkcji oraz do inspekcji i modyfikowania zasobów gotowych do produkcji w przypadku debugowania aplikacji.

 Poniżej znajduje się więcej informacji na temat rodzajów zasobów, z którymi można korzystać w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

### <a name="images-and-textures"></a>Obrazy i tekstury
 Obrazy i tekstury zawierają szczegóły dotyczące kolorów i wizualizacji w grach i aplikacjach. W przypadku grafiki trójwymiarowej tekstury są dostępne w różnych formatach, typach i geometrie w celu obsługi różnych celów. Na przykład normalne mapy zapewniają normalną powierzchnię dla poszczególnych pikseli w celu uzyskania bardziej szczegółowego oświetlenia modeli trójwymiarowych, a mapy modułów zapewniają teksturę we wszystkich kierunkach, takich jak opakowanie, przeznaczenie, odbicie i mapa tekstury sferycznej. Tekstury mogą udostępniać mapy MIP do obsługi wydajnego renderowania na różnych poziomach szczegółowości i mogą obsługiwać różne kanały kolorów i kolejność kolorów. Tekstury mogą być przechowywane w różnych skompresowanych formatach, które zajmują mniej dedykowaną pamięć graficzną i są bardziej wydajne.

 Możesz użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora obrazów do pracy z obrazami i teksturami w wielu wspólnych typach i formatach.

### <a name="3-d-models"></a>modele 3-D
 modele trójwymiarowe tworzą miejsce i kształt w grach i aplikacjach. Co najmniej modele zakodować pozycje punktów w 3-D, które są znane jako *wierzchołki*— wraz z danymi indeksowania, aby definiować linie lub Trójkąty reprezentujące kształt modelu. Dodatkowe dane można kojarzyć z tymi wierzchołkami — na przykład informacje o kolorach, wektorach normalnych lub atrybuty specyficzne dla aplikacji. Każdy model może również definiować atrybuty na poziomie obiektu — na przykład, który moduł cieniujący służy do obliczenia wyglądu powierzchni obiektu lub do której jest stosowana tekstura.

 Można użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytora modelu do pracy z modelami 3-D w kilku wspólnych formatach.

### <a name="shaders"></a>Programy do cieniowania
 Programy do cieniowania są niewielkimi programami specyficznymi dla domeny, które działają w procesorze GPU. Programy do cieniowania określają, jak modele trójwymiarowe są przekształcane na kształty na ekranie i jak kolorowe są poszczególne piksele w tych kształtach. Tworząc cieniowanie i stosując je do obiektu w grze lub aplikacji, możesz nadać obiektowi unikatowy wygląd.

 Możesz użyć projektanta programu do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cieniowania, który jest narzędziem do projektowania cieniowania opartym na grafie, w celu utworzenia niestandardowych efektów wizualnych bez znajomości programowania HLSL.

> [!NOTE]
> Aby uzyskać więcej informacji na temat rozpoczynania pracy z programowaniem DirectX, zobacz [DirectX](https://msdn.microsoft.com/library/ee663274(VS.85).aspx). Aby uzyskać więcej informacji na temat debugowania aplikacji opartych na technologii DirectX, zobacz [Diagnostyka grafiki (Debugowanie grafiki DirectX)](../debugger/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>Zgodność wersji programu DirectX
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używa DirectX do renderowania zasobów 2-D i 3-D. Można wybrać moduł renderujący programu DirectX 11 lub program Windows Advanced rasteryzacji platform (Wypaczenie). Moduł renderowania DirectX 11 zapewnia wysoką wydajność, przyspieszanie sprzętowe w przypadku procesorów DirectX 11 i DirectX 10. Moduł renderowania ZNIEKSZTAŁCAnia pomaga upewnić się, że zasoby współpracują z szeroką gamą komputerów — dotyczy to również komputerów, które nie mają nowoczesnego sprzętu graficznego i komputerów z zintegrowanym sprzętem grafiki. Aby uzyskać więcej informacji na temat wypaczania, zobacz [Przewodnik dotyczący platformy Windows Advanced rasteryzacji](https://msdn.microsoft.com/library/gg615082(VS.85).aspx).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z obrazami i teksturami](../designers/working-with-textures-and-images.md)|Opisuje, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] programu do pracy z obrazami i teksturami.|
|[Praca z modelami 3-D](../designers/working-with-3-d-models.md)|Opisuje, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] programu do pracy z modelami 3-D.|
|[Praca z cieniowaniem](../designers/working-with-shaders.md)|Opisuje, w jaki sposób używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektanta cieniowania do tworzenia i modyfikowania niestandardowych efektów cieniowania.|
|[Korzystanie z obiektów 3-D w grach i aplikacjach](../designers/using-3-d-assets-in-your-game-or-app.md)|Opisuje sposób używania zasobów, które zostały utworzone przy użyciu edytora obrazów, edytora modelu lub projektanta programu do cieniowania, w grze lub aplikacji.|
