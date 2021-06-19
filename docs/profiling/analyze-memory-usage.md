---
title: Analizowanie użycia pamięci
description: Dowiedz się więcej o narzędziach, których można użyć do znalezienia przecieków pamięci i nieefektywnego użycia pamięci, takich jak narzędzie Użycie pamięci i narzędzie alokacji obiektów .NET.
ms.custom: SEO-VS-2020
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a6af0cd98e69a3c43ba70f5609567243e6285201
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387973"
---
# <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

Aby znaleźć przecieki pamięci i niewydajne użycie pamięci, można użyć narzędzi, takich jak narzędzie diagnostyczne użycie pamięci zintegrowane z debugerem lub narzędzia w narzędziu profiler wydajności takie jak narzędzie alokacji obiektów .NET i narzędzie użycie pamięci po mortem.

Narzędzie Użycie pamięci umożliwia tworzenie  co najmniej jednej migawki sterty pamięci zarządzanej i natywnej. Możesz zbierać migawki aplikacji .NET, ASP.NET, C++ lub aplikacji w trybie mieszanym (.NET i natywnych). Narzędzie **Użycie pamięci** można uruchomić w otwartym projekcie Visual Studio, w zainstalowanej Microsoft Store aplikacji lub dołączonej do uruchomionej aplikacji bądź procesu. Narzędzie Użycie **pamięci** można uruchomić z debugowaniem lub bez debugowania. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) W debugerze można włączać i wyłączać profilowanie pamięci oraz zobaczyć podział użycia pamięci dla 1 obiektu. Wyniki użycia pamięci można wyświetlić, gdy wykonywanie jest wstrzymane, na przykład w punkcie przerwania.

Deweloperzy .NET mogą wybrać narzędzie alokacji obiektów .NET lub [narzędzie użycie](../profiling/memory-usage.md) pamięci.

- Narzędzie [przydzielania obiektów .NET](../profiling/dotnet-alloc-tool.md) ułatwia identyfikowanie wzorców alokacji i anomalii w kodzie .NET oraz pomaga identyfikować typowe problemy dotyczące wyrzucania elementów bezużytecznych. To narzędzie działa tylko jako narzędzie post mortem. To narzędzie można uruchomić na maszynach lokalnych lub zdalnych.
- Narzędzie [Użycie pamięci jest](../profiling/memory-usage-without-debugging2.md) przydatne w identyfikowaniu przecieków pamięci, które zwykle nie są typowe w aplikacjach .NET. Jeśli podczas sprawdzania pamięci musisz używać funkcji debugera, takich [](../profiling/memory-usage.md) jak wykonywanie krokowe kodu, zalecane jest użycie pamięci zintegrowane z debugerem.

Deweloperzy języka C++ mogą używać narzędzia użycie pamięci zintegrowanej z debugerem lub bez debugera.

- [Analizowanie użycia pamięci za pomocą debugera](../profiling/memory-usage.md)
- [Analizowanie użycia pamięci bez debugera](../profiling/memory-usage-without-debugging2.md)

Narzędzi profilowania można używać bez debugera w systemie Windows 7 lub nowszym. Windows 8 i nowsze są wymagane do uruchamiania narzędzi profilowania za pomocą debugera (**narzędzia diagnostyczne** okno).

## <a name="blogs-and-videos"></a>Blogi i filmy wideo

[Analizowanie procesora i pamięci podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: Profilowanie pamięci w Visual C++ 2015 r.](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Zobacz też

- [Profilowanie w Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
