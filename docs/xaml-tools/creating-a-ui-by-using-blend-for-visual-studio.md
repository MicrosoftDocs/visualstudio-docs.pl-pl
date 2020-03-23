---
title: Przewodnik funkcji Programu Blend for Visual Studio
titleSuffix: ''
ms.date: 07/31/2019
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2b9f38d83befcf49ecd3de8da3a2cd26ff3ab46
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301672"
---
# <a name="blend-for-visual-studio-overview"></a>Omówienie programu Blend for Visual Studio

Program Blend for Visual Studio ułatwia projektowanie aplikacji windows i sieci Web opartych na języku XAML. Zapewnia takie samo podstawowe środowisko projektowania XAML jak Visual Studio i dodaje projektantów wizualnych dla zaawansowanych zadań, takich jak animacje i zachowania. Aby uzyskać porównanie między programem Blend i Visual Studio, zobacz [Projektowanie XAML w programie Visual Studio i Blend for Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md).

Blend for Visual Studio jest składnikiem programu Visual Studio. Aby zainstalować blend, w **Instalatorze programu Visual Studio** wybierz opcję **deweloperskie platformy uniwersalnej systemu Windows** lub obciążenie **programistyczne pulpitu .NET.** Oba te obciążenia obejmują składnik Blend for Visual Studio.

![Składniki obciążenia platformy uniwersalnej systemu Windows](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Składniki obciążenia programistycznego platformy .NET](media/installer-dotnet-desktop.png)

Jeśli jesteś nowym użytkownikiem programu Blend for Visual Studio, poświęć chwilę na zapoznanie się z unikatowymi funkcjami obszaru roboczego. Ten temat zabierze Cię w szybką wycieczkę.

## <a name="tools-panel"></a>Panel narzędzi

Panel **Narzędzia** w programie Blend dla programu Visual Studio służy do tworzenia i modyfikowania obiektów w aplikacji. Panel **Narzędzia** jest wyświetlany po lewej stronie projektanta XAML, gdy plik *.xaml* jest otwarty.

Obiekty można utworzyć, zaznaczając narzędzie i rysując na obszarze roboczym za pomocą myszy.

![Panel Narzędzia w programie Blend for Visual Studio](media/blend-tools-panel.png)

> [!TIP]
> Niektóre narzędzia w panelu **Narzędzia** mają odmiany, na przykład zamiast prostokąta można wybrać elipsę lub linię. Aby uzyskać dostęp do tych odmian, kliknij prawym przyciskiem myszy lub kliknij i przytrzymaj narzędzie.
>
> ![Różnice narzędzi kształtu w programie Blend for Visual Studio](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>Narzędzia wyboru

Zaznacz obiekty i ścieżki. Narzędzie **Zaznaczanie bezpośrednie** służy do zaznaczania zagnieżdżonych obiektów i segmentów ścieżek.

### <a name="view-tools"></a>Wyświetlanie narzędzi

Dostosuj widok obszaru roboczego, na przykład do przesuwania i powiększania.

### <a name="brush-tools"></a>Narzędzia pędzla

Praca z atrybutami wizualnymi obiektu, takimi jak przekształcanie pędzla lub stosowanie gradientu.

### <a name="object-tools"></a>Narzędzia obiektów

Narysuj najczęściej występujące obiekty w obszarze roboczym, takie jak ścieżki, kształty, panele układu, tekst i formanty.

### <a name="asset-tools"></a>Narzędzia zasobów

Dostęp do okna Zasoby i wyświetlanie ostatnio używanego zasobu z biblioteki.

## <a name="assets-window"></a>Okno Zasoby

**Okno Zasoby** zawiera wszystkie dostępne formanty i jest podobny do **przybornika** w programie Visual Studio. Oprócz formantów w oknie **Zasoby** znajdziesz wszystko, co można dodać do obszaru roboczego, w tym style, multimedia, zachowania i efekty. Aby otworzyć okno **Zasoby,** wybierz polecenie **Wyświetl** > **okno Zasoby** lub naciśnij **klawisze Ctrl**+**Alt**+**X**.

![Okno Zasoby w programie Blend for Visual Studio](media/blend-assets-window.png)

- Wprowadź tekst w polu **Zasoby wyszukiwania,** aby filtrować listę zasobów.
- Przełączanie między trybem siatki a widokiem widoku trybu listy zasobów za pomocą przycisków w prawym górnym rogu.

## <a name="objects-and-timeline-window"></a>Obiekty i okno osi czasu

To okno służy do organizowania obiektów w obszaru roboczego i, jeśli chcesz, do animowania ich. Aby otworzyć okno **Obiekty i oś czasu,** wybierz pozycję **Wyświetl** > **konspekt dokumentu**. Oprócz funkcji podanych w [oknie Konspekt dokumentu](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) w programie Visual Studio, obiekty i oś czasu okna w Blend for Visual Studio ma obszar kompozycji osi czasu po prawej stronie. Podczas tworzenia i edytowania animacji należy używać osi czasu.

![Okno obiekt i oś czasu w trybie animacji](media/storyboard-timeline.png)

Używanie przycisków związanych z scenorysem ![Przyciski scenorysu w programie Blend for Visual Studio](media/storyboard-buttons.png) , aby utworzyć, usunąć, zamknąć lub wybrać scenorys. Użyj obszaru kompozycji osi czasu po prawej stronie, aby wyświetlić oś czasu i przenieść klatki kluczowe.

Umieść wskaźnik myszy na każdym przycisku w oknie, aby dowiedzieć się więcej o dostępnych funkcjach.

## <a name="see-also"></a>Zobacz też

- [Animowanie obiektów](../xaml-tools/animate-objects-in-xaml-designer.md)
- [Rysowanie kształtów i ścieżek](../xaml-tools/draw-shapes-and-paths.md)
- [Projektowanie XAML w programach Visual Studio i Blend for Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md)
