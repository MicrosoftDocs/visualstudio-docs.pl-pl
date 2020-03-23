---
title: Skrócenie czasu uruchamiania
ms.date: 11/15/2017
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 4824939b4ef3ed1bc7fa48b2508fc891c984a3c5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301868"
---
# <a name="optimize-visual-studio-startup-time"></a>Optymalizacja czasu uruchamiania programu Visual Studio

Visual Studio jest przeznaczony do uruchamiania tak szybko i wydajnie, jak to możliwe. Jednak niektóre rozszerzenia programu Visual Studio i okna narzędzi może niekorzystnie wpłynąć na czas uruchamiania podczas ich ładowania. W oknie dialogowym Zarządzanie wydajnością programu **Visual Studio** można kontrolować zachowanie wolnych rozszerzeń i okien narzędzi. Aby uzyskać bardziej ogólne wskazówki dotyczące poprawy wydajności, zobacz [Porady i wskazówki dotyczące wydajności programu Visual Studio.](../ide/visual-studio-performance-tips-and-tricks.md)

## <a name="startup-behavior"></a>Zachowanie podczas uruchamiania

Aby uniknąć wydłużenia czasu uruchamiania, visual studio ładuje rozszerzenia przy użyciu podejścia _na żądanie._ To zachowanie oznacza, że rozszerzenia nie otwierają się natychmiast po uruchomieniu programu Visual Studio, ale zgodnie z potrzebami. Ponadto ponieważ okna narzędzi pozostawione otwarte w poprzedniej sesji programu Visual Studio może spowolnić czas uruchamiania, Visual Studio otwiera okna narzędzi w bardziej inteligentny sposób, aby uniknąć wpływu na czas uruchamiania.

Jeśli program Visual Studio wykryje powolne uruchamianie, zostanie wyświetlony komunikat wyskakujący z ostrzeżeniem o rozszerzeniu lub oknie narzędzia, które powoduje spowolnienie. Komunikat zawiera łącze do okna dialogowego **Zarządzanie wydajnością programu Visual Studio.** Dostęp do tego okna dialogowego można również uzyskać, wybierając **pozycję Pomoc w** > **zarządzaniu wydajnością programu Visual Studio** na pasku menu.

![Zarządzanie wydajnością programu Visual Studio — wyskakujące okienko "Zauważyliśmy, że rozszerzenie ... spowalnia program Visual Studio'](../ide/media/vside_perfdialog_popup.png)

W oknie dialogowym wymieniono rozszerzenia i narzędzia systemu Windows, które mają wpływ na wydajność uruchamiania. Można zmienić ustawienia rozszerzenia i okna narzędzia, aby poprawić wydajność uruchamiania.

## <a name="to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Aby zmienić ustawienia rozszerzenia w celu zwiększenia wydajności uruchamiania, ładowania rozwiązania i wpisywania tekstu

1. Otwórz okno dialogowe **Zarządzanie wydajnością programu Visual Studio,** wybierając **pozycję Pomoc w** > **zarządzaniu wydajnością programu Visual Studio** na pasku menu.

    Jeśli rozszerzenie spowalnia uruchamianie programu Visual Studio, ładowanie lub wpisywanie, rozszerzenie pojawi się w oknie dialogowym **Zarządzanie wydajnością programu Visual Studio** w obszarze**Uruchamianie** **rozszerzeń** > (lub **Ładowanie rozwiązania** lub **Wpisywanie**tekstu).

    ![Zarządzanie wydajnością programu Visual Studio — widok rozszerzeń](../ide/media/vside_perfdialog_extensions.png)

2. Wybierz rozszerzenie, które chcesz wyłączyć, a następnie wybierz przycisk **Wyłącz.**

Zawsze można ponownie włączyć rozszerzenie dla przyszłych sesji przy użyciu **Menedżera rozszerzeń** lub okna dialogowego **Zarządzanie wydajnością programu Visual Studio.**

## <a name="to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Aby zmienić ustawienia okna narzędzia w celu skrócenia czasu uruchamiania

1. Otwórz okno dialogowe **Zarządzanie wydajnością programu Visual Studio,** wybierając **pozycję Pomoc w** > **zarządzaniu wydajnością programu Visual Studio** na pasku menu.

    Jeśli okno narzędzia spowalnia uruchamianie programu Visual Studio, w oknie dialogowym **Zarządzanie wydajnością programu Visual Studio** w obszarze**Uruchamianie** **narzędzia systemu Windows** > pojawi się okno narzędzia .

2. Wybierz okno narzędzia, dla którego chcesz zmienić zachowanie.

3. Wybierz jedną z następujących trzech opcji:

   - **Użyj zachowania domyślnego:** Domyślne zachowanie okna narzędzia. Utrzymanie tej opcji wybraną nie poprawi wydajności uruchamiania.

   - **Nie pokazuj okna przy starcie:** Okno określonego narzędzia jest zawsze zamykane po otwarciu programu Visual Studio, nawet jeśli zostało ono otwarte w poprzedniej sesji. Okno narzędzia można otworzyć z odpowiedniego menu, gdy jest to potrzebne.

   - **Automatyczne ukrywanie okna podczas uruchamiania:** Jeśli okno narzędzia zostało otwarte w poprzedniej sesji, ta opcja zwija grupę okna narzędzia podczas uruchamiania, aby uniknąć inicjowania okna narzędzia. Ta opcja jest dobrym wyborem, jeśli często używasz okna narzędzia. Okno narzędzia jest nadal dostępne, ale nie wpływa już negatywnie na czas uruchamiania programu Visual Studio.

     ![Zarządzanie wydajnością programu Visual Studio — widok systemu windows narzędzi](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Niektóre wcześniejsze wersje programu Visual Studio 2017 miały funkcję o nazwie **lekkie obciążenie rozwiązania.** W bieżących wersjach duże rozwiązania, które zawierają zarządzany kod, ładują się znacznie szybciej niż poprzednio, nawet bez lekkiego obciążenia rozwiązania.

## <a name="see-also"></a>Zobacz też

- [Optymalizowanie wydajności programu Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Porady i wskazówki dotyczące wydajności programu Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog programu Visual Studio — szybsze ładowanie rozwiązań za pomocą programu Visual Studio 2017 w wersji 15.6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
