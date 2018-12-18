---
title: Zwiększyć wydajność, jeśli program Visual Studio jest powolne
titleSuffix: ''
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.performancecenter
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f5fe9324360a01700024e14e6c70755d61aa3e60
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065778"
---
# <a name="optimize-visual-studio-performance"></a>Optymalizacja wydajności programu Visual Studio

Ten artykuł zawiera wskazówki, aby wypróbować, jeśli okaże się, że program Visual Studio działa wolno. Możesz również skorzystać z przyjrzeć się [i porady dotyczące wydajności programu Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md) Aby uzyskać więcej wskazówek na temat sposobu zwiększenia wydajności.

## <a name="upgrade-to-visual-studio-2017-version-156-or-later"></a>Uaktualnianie do programu Visual Studio 2017 w wersji 15.6 lub nowszej

Jeśli obecnie używasz programu Visual Studio 2015, Pobierz [programu Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) bezpłatnie, aby zapoznaj się z jego lepszą wydajność. Rozwiązania załadować dwóch do trzech razy szybciej w programie Visual Studio 2017 o ulepszenia wydajności w innych obszarach zbyt. Visual Studio 2017 jest side-by-side zgodny z programu Visual Studio 2015, dzięki czemu nie będzie utracie danych dzięki eksperymentom.

Jeśli obecnie używasz programu Visual Studio 2017, upewnij się, że używasz wersji 15.6 lub nowszej. Dane pokazują, że rozwiązania ładować się dwa lub trzy razy szybszy w wersji 15.6. Pobierz go [tutaj](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

## <a name="extensions-and-tool-windows"></a>Rozszerzenia i okna narzędzi

Masz zainstalowanych rozszerzeń, które zmniejszają programu Visual Studio. Aby uzyskać pomoc dotyczącą zarządzanie rozszerzeniami w celu zwiększenia wydajności, zobacz [zmiany ustawień rozszerzenia w celu zwiększenia wydajności](../ide/optimize-visual-studio-startup-time.md#extensions).

Podobnie może być okien narzędzi, które zmniejszają programu Visual Studio. Aby uzyskać pomoc na temat zarządzania okien narzędzi, zobacz [zmiany ustawień okna narzędzi, aby zwiększyć wydajność](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Sprzęt

Jeśli myślisz o uaktualnienie sprzętu, dysku półprzewodnikowym (SSD) ma więcej wpływ na wydajność niż więcej pamięci RAM lub szybszy Procesor.

Jeśli zostaną dodane dyski SSD, aby uzyskać optymalną wydajność należy zainstalować Windows na tym dysku, a nie na dysku twardym (HDD). Lokalizację dysku rozwiązań programu Visual Studio nie wydaje się niezależnie od tego, jak najwięcej.

Ponadto nie należy uruchamiać swoje rozwiązanie z dysku USB. Skopiuj go na dysk twardy lub dysk SSD.

## <a name="help-us-improve"></a>Pomóż nam w usprawnianiu

Twoja opinia pomoże nam poprawić. Użyj **Zgłoś Problem** funkcji "Zapisz" Śledzenie i wysyłanie do nas. Wybierz ikonę opinii **szybkiego uruchamiania**, lub wybierz **pomocy** > **Wyślij opinię** > **Zgłoś Problem** z paska menu. Aby uzyskać więcej informacji, zobacz [jak zgłosić problem w programie Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>Zobacz także

- [Porady i wskazówki](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog Visual Studio — rozwiązania obciążenia szybciej za pomocą programu Visual Studio 2017 w wersji 15.6](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)