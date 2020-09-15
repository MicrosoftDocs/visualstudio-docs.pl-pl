---
title: Analizowanie użycia pamięci
ms.custom: seodec18
ms.date: 03/30/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77fa9087673ff8e9a429caa27318a60f21d4a60
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075447"
---
# <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

Aby wyszukać przecieki pamięci i niewydajne użycie pamięci, można użyć narzędzi, takich jak narzędzie do diagnostyki użycia pamięci zintegrowanej z debugerem lub narzędzia w profilerze wydajności, takie jak narzędzie alokacji obiektów .NET i narzędzie do użycia pamięci.

Narzędzie użycie pamięci umożliwia wykonanie co najmniej jednej *migawki* zarządzanego i natywnego sterty pamięci. Można zbierać migawki aplikacji platformy .NET, ASP.NET, natywnych lub mieszanych (.NET i Native). Narzędzie **użycie pamięci** można uruchomić w otwartym projekcie programu Visual Studio, w zainstalowanej aplikacji Microsoft Store lub dołączone do uruchomionej aplikacji lub procesu. Narzędzie **użycie pamięci** można uruchomić z debugowaniem lub bez niego. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). W debugerze można włączać i wyłączać Profilowanie pamięci oraz wyświetlać podział poszczególnych obiektów w pamięci. Wyniki użycia pamięci można wyświetlić po wstrzymaniu wykonywania, na przykład w punkcie przerwania.

Narzędzie **alokacji obiektów platformy .NET** pomaga identyfikować wzorce i anomalie alokacji w kodzie .NET. To narzędzie jest uruchamiane tylko jako narzędzie po zakończeniu. To narzędzie można uruchomić na komputerze lokalnym lub zdalnym.

Aby uzyskać szczegółowe instrukcje opisujące sposób korzystania z narzędzi analizy pamięci, zobacz samouczek [Analizowanie użycia pamięci](../profiling/memory-usage.md) i narzędzie do [alokacji obiektów platformy .NET](../profiling/dotnet-alloc-tool.md).

Narzędzi profilowania można używać bez debugera z systemem Windows 7 i nowszymi wersjami. System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno**Narzędzia diagnostyczne** ).

## <a name="blogs-and-videos"></a>Blogi i filmy wideo

[Analizuj procesor i pamięć podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog Visual C++: Profilowanie pamięci w Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Zobacz także

- [Analizowanie użycia pamięci bez debugera](../profiling/memory-usage-without-debugging2.md)
- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
