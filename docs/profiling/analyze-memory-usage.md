---
title: Analizowanie użycia pamięci
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43126f4bba8afc50fc5c1e4cf6a3b9a67c6f340c
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233061"
---
# <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

aby znaleźć przecieki pamięci i nieefektywne użycie pamięci, można użyć narzędzi, takich jak narzędzie diagnostyczne użycia pamięci zintegrowane z debugerem lub narzędzia w programie Performance Profiler, takie jak narzędzie .NET Object Allocation i narzędzie pośmiertne Użycie pamięci.

Narzędzie Użycie pamięci umożliwia podjęcie co najmniej jednej *migawki* zarządzanej i natywnej sterty pamięci. Można zbierać migawki aplikacji .NET, ASP.NET, natywnych lub mieszanych (NET i natywnych). Narzędzie **Użycie pamięci** można uruchomić w otwartym projekcie programu Visual Studio, w zainstalowanej aplikacji Microsoft Store lub dołączone do uruchomionej aplikacji lub procesu. Narzędzie można uruchomić na komputerach lokalnych lub zdalnych lub na symulatorze lub emulatorze. Narzędzie Użycie **pamięci** można uruchomić z debugowaniem lub bez. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). W debugerze można włączać i wyłączać profilowanie pamięci i zobaczyć podział użycia pamięci na obiekt. Można wyświetlić wyniki użycia pamięci, gdy wykonanie jest wstrzymane, na przykład w punkcie przerwania.

Narzędzie **.NET Object Allocation** ułatwia identyfikowanie wzorców alokacji i anomalii w kodzie platformy .NET. To narzędzie działa tylko jako narzędzie pośmiertne.

Aby uzyskać szczegółowe instrukcje opisujące sposób korzystania z narzędzi do analizy pamięci, zobacz Samouczek [Analizowanie użycia pamięci](../profiling/memory-usage.md) i [narzędzie .NET Object Allocation](../profiling/dotnet-alloc-tool.md).

Narzędzia profilowania można używać bez debugera w systemie Windows 7 i nowszych. System Windows 8 i nowsze są wymagane do uruchamiania narzędzi profilowania za pomocą debugera (okno**Narzędzia diagnostyczne).**

## <a name="blogs-and-videos"></a>Blogi i filmy

[Analizowanie procesora i pamięci podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: Profilowanie pamięci w języku Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
- [Analizowanie użycia pamięci bez debugera](../profiling/memory-usage-without-debugging2.md)
