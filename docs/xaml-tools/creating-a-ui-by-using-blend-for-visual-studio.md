---
title: Samouczek funkcji Blend for Visual Studio
titleSuffix: ''
description: Dowiedz się więcej na temat interfejsu użytkownika obszaru roboczego i funkcji Blend for Visual Studio, składnika służącego do projektowania aplikacji systemu Windows i sieci Web opartych na języku XAML.
ms.custom: SEO-VS-2020
ms.date: 07/31/2019
ms.topic: overview
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: affef27dae9fe569c0cacbbd3725b9bf76edb94c
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796345"
---
# <a name="blend-for-visual-studio-overview"></a>Przegląd Blend for Visual Studio

Blend for Visual Studio ułatwia projektowanie aplikacji sieci Web opartych na języku XAML. Zapewnia to takie samo podstawowe środowisko projektowe XAML jak program Visual Studio i dodaje projektantów wizualizacji do zaawansowanych zadań, takich jak animacje i zachowania. Aby uzyskać porównanie między programem Blend i programem Visual Studio, zobacz [Designing XAML in Visual Studio i Blend for Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md).

Blend for Visual Studio jest składnikiem programu Visual Studio. Aby zainstalować program Blend, w **Instalator programu Visual Studio** wybierz **platforma uniwersalna systemu Windows programowanie** lub Programowanie na **platformie .NET** . Oba te obciążenia obejmują składnik Blend for Visual Studio.

![Składniki obciążenia platformy UWP](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Składniki obciążeń programu .NET Desktop Development](media/installer-dotnet-desktop.png)

Jeśli dopiero zaczynasz Blend for Visual Studio, poświęć chwilę na zapoznanie się z unikatowymi funkcjami obszaru roboczego. Ten temat obejmuje Krótki przewodnik.

## <a name="tools-panel"></a>Panel narzędzi

Panel **Narzędzia** w Blend for Visual Studio służy do tworzenia i modyfikowania obiektów w aplikacji. Panel **Narzędzia** pojawia się po lewej stronie projektanta XAML, gdy plik *XAML* jest otwarty.

Obiekty są tworzone przez wybranie narzędzia i rysowanie w obszarze kompozycji za pomocą myszy.

![Panel narzędzia w Blend for Visual Studio](media/blend-tools-panel.png)

> [!TIP]
> Niektóre z narzędzi w panelu **Narzędzia** mają różne odmiany, na przykład zamiast prostokąta, można wybrać elipsę lub linię. Aby uzyskać dostęp do tych odmian, kliknij prawym przyciskiem myszy lub kliknij i przytrzymaj narzędzie.
>
> ![narzędzie Kształt Wariacje w Blend for Visual Studio](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>Narzędzia wyboru

Wybierz obiekty i ścieżki. Użyj narzędzia **wybór bezpośredni** , aby zaznaczyć zagnieżdżone obiekty i segmenty ścieżki.

### <a name="view-tools"></a>Narzędzia widoku

Dostosuj widok obszaru kompozycji, taki jak przesuwanie i powiększanie.

### <a name="brush-tools"></a>Narzędzia pędzla

Pracuj z atrybutami wizualizacji obiektu, takimi jak Przekształcanie pędzla lub stosowanie gradientu.

### <a name="object-tools"></a>Narzędzia obiektów

Rysowanie najpopularniejszych obiektów w obszarze kompozycji, takich jak ścieżki, kształty, panele układu, tekst i kontrolki.

### <a name="asset-tools"></a>Narzędzia zasobów

Uzyskaj dostęp do okna składniki i Pokaż ostatnio używany element zawartości z biblioteki.

## <a name="assets-window"></a>Okno zasobów

Okno **składniki** zawiera wszystkie dostępne kontrolki podobne do **przybornika** w programie Visual Studio. Oprócz formantów znajdziesz wszystkie elementy, które można dodać do obszaru kompozycji, w oknie **zasoby** , w tym style, multimedia, zachowania i efekty. Aby otworzyć okno **zasoby** , wybierz pozycję **Wyświetl**  >  **okno składniki** lub naciśnij **klawisze CTRL** + **Alt** + **X** .

![Okno elementów zawartości w Blend for Visual Studio](media/blend-assets-window.png)

- Wprowadź tekst w polu **Wyszukaj zasoby** , aby przefiltrować listę zasobów.
- Przełączanie między trybem siatki a widokiem widoku listy zasobów przy użyciu przycisków w prawym górnym rogu.

## <a name="objects-and-timeline-window"></a>Okno Obiekty i oś czasu

To okno służy do organizowania obiektów w obszarze kompozycji i, jeśli chcesz, animowania ich. Aby otworzyć okno **obiekty i oś czasu** , wybierz pozycję **Wyświetl**  >  **Konspekt dokumentu** . Poza funkcjami dostępnymi w [oknie Konspekt dokumentu](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) w programie Visual Studio, okno Obiekty i oś czasu w Blend for Visual Studio ma obszar kompozycji osi czasu po prawej stronie. Użyj osi czasu podczas tworzenia i edytowania animacji.

![Okno obiektu i osi czasu w trybie animacji](media/storyboard-timeline.png)

Korzystanie z przycisków związanych z scenorysem ![Przyciski scenorysu w Blend for Visual Studio](media/storyboard-buttons.png) Aby utworzyć, usunąć, zamknąć lub wybrać scenorys. Użyj obszaru kompozycji osi czasu po prawej stronie, aby wyświetlić oś czasu i przenieść ramki kluczowe.

Umieść kursor nad każdym przyciskiem w oknie, aby dowiedzieć się więcej o dostępnych funkcjach.

## <a name="see-also"></a>Zobacz także

- [Animowanie obiektów](../xaml-tools/animate-objects-in-xaml-designer.md)
- [Rysowanie kształtów i ścieżek](../xaml-tools/draw-shapes-and-paths.md)
- [Projektowanie XAML w programach Visual Studio i Blend for Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md)
