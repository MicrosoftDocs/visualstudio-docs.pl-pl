---
title: Zwiększenie wydajności, jeśli program Visual Studio działa wolno
titleSuffix: ''
description: Dowiedz się, jak poprawić wydajność programu Visual Studio, jeśli okaże się, że działa wolno.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6e6f93b7709144e6682bc54d5686fde5ff650f56
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871473"
---
# <a name="optimize-visual-studio-performance"></a>Optymalizowanie wydajności programu Visual Studio

W tym artykule przedstawiono kilka sugestii, które należy podjąć, jeśli okaże się, że program Visual Studio działa wolno. Możesz również zapoznać się z [poradami i wskazówkami dotyczącymi wydajności programu Visual Studio,](../ide/visual-studio-performance-tips-and-tricks.md) Aby uzyskać więcej sugestii dotyczących poprawy wydajności.

## <a name="upgrade-visual-studio"></a>Uaktualnij program Visual Studio

Jeśli obecnie używasz programu Visual Studio 2015, Pobierz [program Visual studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) lub [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) bezpłatnie, aby sprawdzić jego zwiększoną wydajność. Rozwiązania są ładowane od dwóch do trzech razy szybciej niż w programie Visual Studio 2015, a także ulepszenia wydajności w innych obszarach. Program Visual Studio 2017 i program Visual Studio 2019 są zgodne ze standardami programu Visual Studio 2015, więc nie utracisz żadnych prób.

::: moniker range="vs-2017"

Jeśli używasz już programu Visual Studio 2017, upewnij się, że korzystasz z wersji 15,6 lub nowszej. Dane pokazują, że rozwiązania ładowane do dwóch lub trzech razy szybciej w wersji 15,6. Pobierz je [tutaj](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Rozszerzenia i okna narzędzi

Być może zainstalowano rozszerzenia, które spowalniają działanie programu Visual Studio. Aby uzyskać pomoc dotyczącą zarządzania rozszerzeniami w celu zwiększenia wydajności, zobacz [Zmiana ustawień rozszerzenia w celu zwiększenia wydajności](../ide/optimize-visual-studio-startup-time.md#extensions).

Podobnie możesz mieć okna narzędzi, które spowalniają działanie programu Visual Studio. Aby uzyskać pomoc dotyczącą zarządzania oknami narzędzi, zobacz [Zmień ustawienia okna narzędzi, aby zwiększyć wydajność](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Sprzęt

Jeśli zastanawiasz się nad uaktualnianiem sprzętu, dysk półprzewodnikowy (SSD) ma większy wpływ na wydajność niż dodatkowa pamięć RAM lub szybszy procesor CPU.

W przypadku dodania dysku SSD w celu uzyskania optymalnej wydajności instalacji systemu Windows na tym dysku, w przeciwieństwie do dysków twardych (dysk twardy). Lokalizacja dysku rozwiązań programu Visual Studio nie ma znaczenia.

Ponadto nie należy uruchamiać rozwiązania z dysku USB. Skopiuj go na dysk twardy lub dysk SSD.

## <a name="help-us-improve"></a>Pomóż nam udoskonalić

Twoja opinia pomoże nam ulepszyć program. Użyj funkcji **Zgłoś problem** , aby "zarejestrować" śledzenie i wysłać do nas. Wybierz ikonę opinii obok pozycji **Szybkie uruchamianie** lub wybierz pozycję **Pomoc**  >  **Wyślij opinię**  >  **Zgłoś problem** z paska menu. Aby uzyskać więcej informacji, zobacz [Jak zgłosić problem w programie Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Porady i wskazówki dotyczące wydajności](../ide/visual-studio-performance-tips-and-tricks.md)
- [Rozwiązania do ładowania blogów z programu Visual Studio szybciej dzięki programowi Visual Studio 2017 w wersji 15,6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
