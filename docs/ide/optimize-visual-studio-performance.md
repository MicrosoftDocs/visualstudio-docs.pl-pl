---
title: Zwiększyć wydajność, jeśli program Visual Studio jest powolne
titleSuffix: ''
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 193343c8fce810280f380b11a72b7cb6892ef18e
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223775"
---
# <a name="optimize-visual-studio-performance"></a>Optymalizacja wydajności programu Visual Studio

Ten artykuł zawiera wskazówki, aby wypróbować, jeśli okaże się, że program Visual Studio działa wolno. Możesz również skorzystać z przyjrzeć się [i porady dotyczące wydajności programu Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md) Aby uzyskać więcej wskazówek na temat sposobu zwiększenia wydajności.

## <a name="upgrade-visual-studio"></a>Uaktualnij program Visual Studio

Jeśli obecnie używasz programu Visual Studio 2015, Pobierz [programu Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) lub [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) bezpłatnie, aby zapoznaj się z jego lepszą wydajność. Rozwiązania załadować dwóch do trzech razy szybciej niż w programie Visual Studio 2015 za pomocą ulepszenia wydajności w innych obszarach zbyt. Visual Studio 2017 i Visual Studio 2019 r są zgodne side-by-side przy użyciu programu Visual Studio 2015, dzięki czemu nie będzie utracie danych dzięki eksperymentom.

::: moniker range="vs-2017"

Jeśli już używasz programu Visual Studio 2017, upewnij się, że używasz wersji 15.6 lub nowszej. Dane pokazują, że rozwiązania ładować się dwa lub trzy razy szybszy w wersji 15.6. Pobierz go [tutaj](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017).

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Rozszerzenia i okna narzędzi

Masz zainstalowanych rozszerzeń, które zmniejszają programu Visual Studio. Aby uzyskać pomoc dotyczącą zarządzanie rozszerzeniami w celu zwiększenia wydajności, zobacz [zmiany ustawień rozszerzenia w celu zwiększenia wydajności](../ide/optimize-visual-studio-startup-time.md#extensions).

Podobnie może być okien narzędzi, które zmniejszają programu Visual Studio. Aby uzyskać pomoc na temat zarządzania okien narzędzi, zobacz [zmiany ustawień okna narzędzi, aby zwiększyć wydajność](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Sprzęt

Jeśli myślisz o uaktualnienie sprzętu, dysku półprzewodnikowym (SSD) ma więcej wpływ na wydajność niż więcej pamięci RAM lub szybszy Procesor.

Jeśli zostaną dodane dyski SSD, aby uzyskać optymalną wydajność należy zainstalować Windows na tym dysku, a nie na dysku twardym (HDD). Lokalizację dysku rozwiązań programu Visual Studio nie wydaje się niezależnie od tego, jak najwięcej.

Ponadto nie należy uruchamiać swoje rozwiązanie z dysku USB. Skopiuj go na dysk twardy lub dysk SSD.

## <a name="help-us-improve"></a>Pomóż nam w usprawnianiu

Twoja opinia pomoże nam poprawić. Użyj **Zgłoś Problem** funkcji "Zapisz" Śledzenie i wysyłanie do nas. Wybierz ikonę opinii **szybkiego uruchamiania**, lub wybierz **pomocy** > **Wyślij opinię** > **Zgłoś Problem** z paska menu. Aby uzyskać więcej informacji, zobacz [jak zgłosić problem z programem Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Porady i wskazówki](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog Visual Studio — rozwiązania obciążenia szybciej za pomocą programu Visual Studio 2017 w wersji 15.6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)