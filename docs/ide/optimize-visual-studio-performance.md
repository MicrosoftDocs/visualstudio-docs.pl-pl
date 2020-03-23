---
title: Zwiększ wydajność, jeśli program Visual Studio jest powolny
titleSuffix: ''
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 6495e8506e12c0c5e5f878a23c609fe53a401bde
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596999"
---
# <a name="optimize-visual-studio-performance"></a>Optymalizowanie wydajności programu Visual Studio

Ten artykuł zawiera kilka sugestii, aby spróbować, jeśli okaże się, że visual studio działa wolno. Można również spojrzeć na [porady dotyczące wydajności programu Visual Studio i wskazówki,](../ide/visual-studio-performance-tips-and-tricks.md) aby uzyskać więcej sugestii dotyczących poprawy wydajności.

## <a name="upgrade-visual-studio"></a>Uaktualnianie programu Visual Studio

Jeśli obecnie używasz programu Visual Studio 2015, pobierz [program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) lub [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) bezpłatnie, aby sprawdzić jego zwiększoną wydajność. Rozwiązania ładują się dwa do trzech razy szybciej niż w programie Visual Studio 2015, z poprawą wydajności w innych obszarach. Visual Studio 2017 i Visual Studio 2019 są zgodne obok siebie z programem Visual Studio 2015, więc nic nie stracisz, wypróbowywając go.

::: moniker range="vs-2017"

Jeśli korzystasz już z programu Visual Studio 2017, upewnij się, że używasz wersji 15.6 lub nowszej. Dane pokazują, że rozwiązania ładują się do dwóch lub trzech razy szybciej w wersji 15.6. Pobierz go [tutaj](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Rozszerzenia i okna narzędzi

Być może masz zainstalowane rozszerzenia, które spowalniają program Visual Studio. Aby uzyskać pomoc dotyczącą zarządzania rozszerzeniami w celu zwiększenia wydajności, zobacz [Zmienianie ustawień rozszerzenia](../ide/optimize-visual-studio-startup-time.md#extensions)w celu zwiększenia wydajności .

Podobnie może być okna narzędzi, które spowalniają program Visual Studio w dół. Aby uzyskać pomoc dotyczącą zarządzania oknami narzędzi, zobacz [Zmienianie ustawień okna narzędzia](../ide/optimize-visual-studio-startup-time.md#tool-windows)w celu zwiększenia wydajności .

## <a name="hardware"></a>Sprzęt

Jeśli myślisz o uaktualnieniu sprzętu, dysk PÓŁPRZEWODNIKOWY (SSD) ma większy wpływ na wydajność niż dodatkowa pamięć RAM lub szybszy procesor.

Jeśli dodasz dysk SSD, aby uzyskać optymalną wydajność, zainstaluj system Windows na tym dysku, w przeciwieństwie do dysku twardego (HDD). Lokalizacja dysku rozwiązania programu Visual Studio nie wydaje się mieć tak duże znaczenie.

Ponadto nie należy uruchamiać rozwiązania z dysku USB. Skopiuj go na dysk twardy lub dysk SSD.

## <a name="help-us-improve"></a>Pomóż nam ulepszyć

Twoja opinia pomaga nam się ulepszyć. Funkcja **Zgłoś problem,** aby "zarejestrować" ślad i wysłać do nas. Wybierz ikonę opinii obok **pozycji QuickLaunch**lub wybierz **pozycję Pomóż** > **wysłać opinię Zgłoś** > problem z**paska** menu. Aby uzyskać więcej informacji, zobacz [Jak zgłosić problem z programem Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Porady i wskazówki dotyczące wydajności](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog programu Visual Studio — szybsze ładowanie rozwiązań za pomocą programu Visual Studio 2017 w wersji 15.6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
