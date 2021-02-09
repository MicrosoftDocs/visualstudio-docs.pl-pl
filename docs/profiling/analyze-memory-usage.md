---
title: Analizowanie użycia pamięci
description: Informacje o narzędziach, których można użyć w celu wyszukania przecieków pamięci i niewydajnego użycia pamięci, narzędzi takich jak narzędzie użycie pamięci i narzędzie alokacji obiektów platformy .NET.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2af4bc47d711275716eea528a4d9bd816408322f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901139"
---
# <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

Aby wyszukać przecieki pamięci i niewydajne użycie pamięci, można użyć narzędzi, takich jak narzędzie do diagnostyki użycia pamięci zintegrowanej z debugerem lub narzędzia w profilerze wydajności, takie jak narzędzie alokacji obiektów .NET i narzędzie do użycia pamięci.

Narzędzie użycie pamięci umożliwia wykonanie co najmniej jednej *migawki* zarządzanego i natywnego sterty pamięci. Można zbierać migawki aplikacji platformy .NET, ASP.NET, C++ lub mieszanych (.NET i Native). Narzędzie **użycie pamięci** można uruchomić w otwartym projekcie programu Visual Studio, w zainstalowanej aplikacji Microsoft Store lub dołączone do uruchomionej aplikacji lub procesu. Narzędzie **użycie pamięci** można uruchomić z debugowaniem lub bez niego. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). W debugerze można włączać i wyłączać Profilowanie pamięci oraz wyświetlać podział poszczególnych obiektów w pamięci. Wyniki użycia pamięci można wyświetlić po wstrzymaniu wykonywania, na przykład w punkcie przerwania.

Deweloperzy platformy .NET mogą wybrać jedno z narzędzi do alokacji obiektów .NET lub narzędzia [użycie pamięci](../profiling/memory-usage.md) .

- [Narzędzie alokacji obiektów platformy .NET](../profiling/dotnet-alloc-tool.md) pomaga identyfikować wzorce i anomalie alokacji w kodzie .NET oraz pomaga identyfikować typowe problemy związane z odzyskiwaniem pamięci. To narzędzie jest uruchamiane tylko jako narzędzie po zakończeniu. To narzędzie można uruchomić na komputerze lokalnym lub zdalnym.
- [Narzędzie użycie pamięci](../profiling/memory-usage-without-debugging2.md) jest pomocne w identyfikowaniu przecieków pamięci, które zwykle nie są typowe w aplikacjach .NET. Jeśli musisz użyć funkcji debugera podczas sprawdzania pamięci, na przykład przechodzenie przez kod, zalecane jest narzędzie [użycie pamięci zintegrowanej z debugerem](../profiling/memory-usage.md) .

Deweloperzy języka C++ mogą korzystać z narzędzia do użycia pamięci zintegrowanej z debugerem lub bez debugera.

- [Analizowanie użycia pamięci za pomocą debugera](../profiling/memory-usage.md)
- [Analizowanie użycia pamięci bez debugera](../profiling/memory-usage-without-debugging2.md)

Narzędzi profilowania można używać bez debugera z systemem Windows 7 i nowszymi wersjami. System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno **Narzędzia diagnostyczne** ).

## <a name="blogs-and-videos"></a>Blogi i filmy wideo

[Analizuj procesor i pamięć podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog Visual C++: Profilowanie pamięci w Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
