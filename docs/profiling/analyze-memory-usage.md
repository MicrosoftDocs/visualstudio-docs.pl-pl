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
ms.openlocfilehash: 5ddb082bf2451759be239d5c16404e82bcd84733
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578162"
---
# <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

Aby wyszukać przecieki pamięci i niewydajne użycie pamięci, można użyć narzędzi, takich jak narzędzie do diagnostyki użycia pamięci zintegrowanej z debugerem lub narzędzia w profilerze wydajności, takie jak narzędzie alokacji obiektów .NET i narzędzie do użycia pamięci. Narzędzie użycie pamięci umożliwia wykonanie co najmniej jednej *migawki* zarządzanego i natywnego sterty pamięci. Można zbierać migawki aplikacji platformy .NET, ASP.NET, Tryb natywny lub mieszany (.NET i natywny). 

Narzędzie **użycie pamięci** można uruchomić w otwartym projekcie programu Visual Studio, w zainstalowanej aplikacji Microsoft Store lub dołączone do uruchomionej aplikacji lub procesu. Narzędzie można uruchomić na maszynach lokalnych lub zdalnych lub na symulatorze lub w emulatorze. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Narzędzie **użycie pamięci** można uruchomić z debugowaniem lub bez niego. W debugerze można włączać i wyłączać Profilowanie pamięci oraz wyświetlać podział poszczególnych obiektów w pamięci. Wyniki użycia pamięci można wyświetlić po wstrzymaniu wykonywania, na przykład w punkcie przerwania.

Narzędzie **alokacji obiektów platformy .NET** działa tylko jako narzędzie po stronie programu.

Aby uzyskać szczegółowe instrukcje opisujące sposób korzystania z narzędzi analizy pamięci, zobacz samouczek [Analizowanie użycia pamięci](../profiling/memory-usage.md) i narzędzie do [alokacji obiektów platformy .NET](../profiling/dotnet-alloc-tool.md).

Można użyć narzędzi profilowania bez debugera, system Windows 7 lub nowszy. System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno**Narzędzia diagnostyczne** ).

## <a name="blogs-and-videos"></a>Blogi i filmy wideo

[Analizuj procesor i pamięć podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog C++ wizualny: Profilowanie pamięci C++ w Visual 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
- [Analizowanie użycia pamięci bez debugera](../profiling/memory-usage-without-debugging2.md)
