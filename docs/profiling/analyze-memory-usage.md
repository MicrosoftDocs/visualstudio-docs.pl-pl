---
title: Analizowanie użycia pamięci
ms.custom: seodec18
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0262081489ec6e037a006649c3041baf02b32d58
ms.sourcegitcommit: 172aaf05596a9d8ded298b7b104569c1cce6160e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2020
ms.locfileid: "92007214"
---
# <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

Aby wyszukać przecieki pamięci i niewydajne użycie pamięci, można użyć narzędzi, takich jak narzędzie do diagnostyki użycia pamięci zintegrowanej z debugerem lub narzędzia w profilerze wydajności, takie jak narzędzie alokacji obiektów .NET i narzędzie do użycia pamięci.

Narzędzie użycie pamięci umożliwia wykonanie co najmniej jednej *migawki* zarządzanego i natywnego sterty pamięci. Można zbierać migawki aplikacji platformy .NET, ASP.NET, C++ lub mieszanych (.NET i Native). Narzędzie **użycie pamięci** można uruchomić w otwartym projekcie programu Visual Studio, w zainstalowanej aplikacji Microsoft Store lub dołączone do uruchomionej aplikacji lub procesu. Narzędzie **użycie pamięci** można uruchomić z debugowaniem lub bez niego. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). W debugerze można włączać i wyłączać Profilowanie pamięci oraz wyświetlać podział poszczególnych obiektów w pamięci. Wyniki użycia pamięci można wyświetlić po wstrzymaniu wykonywania, na przykład w punkcie przerwania.

Deweloperzy platformy .NET mogą wybrać między narzędziem [użycie pamięci](../profiling/memory-usage.md) a narzędziem do [alokacji obiektów platformy .NET](../profiling/dotnet-alloc-tool.md).
- Narzędzie **alokacji obiektów platformy .NET** pomaga identyfikować wzorce i anomalie alokacji w kodzie .NET oraz pomaga identyfikować typowe problemy związane z odzyskiwaniem pamięci. To narzędzie jest uruchamiane tylko jako narzędzie po zakończeniu. To narzędzie można uruchomić na komputerze lokalnym lub zdalnym.
- Narzędzie **użycie pamięci** jest pomocne w identyfikowaniu przecieków pamięci, które zwykle nie są typowe w aplikacjach .NET. Jeśli musisz użyć funkcji debugera podczas sprawdzania pamięci, na przykład przechodzenie przez kod, zalecane jest narzędzie [użycie pamięci zintegrowanej z debugerem](../profiling/beginners-guide-to-performance-profiling.md) .

Narzędzi profilowania można używać bez debugera z systemem Windows 7 i nowszymi wersjami. System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno**Narzędzia diagnostyczne** ).

## <a name="blogs-and-videos"></a>Blogi i filmy wideo

[Analizuj procesor i pamięć podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog Visual C++: Profilowanie pamięci w Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Zobacz też

- [Analizowanie użycia pamięci bez debugera](../profiling/memory-usage-without-debugging2.md)
- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
