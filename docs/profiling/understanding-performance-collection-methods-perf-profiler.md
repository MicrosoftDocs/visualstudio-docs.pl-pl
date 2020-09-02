---
title: Omówienie metod zbierania danych wydajności profilera
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: f0e24f3fc33ea456ad02bf9797b934a1a56d4492
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238585"
---
# <a name="understand-profiler-performance-collection-methods"></a>Omówienie metod zbierania danych wydajności profilera

W tym dokumencie opisano metody zbierania danych używane przez narzędzia do oceny wydajności programu Visual Studio. 

## <a name="sampling"></a>Próbkowanie

Metody próbkowania do profilowania zbierają dane statystyczne o pracy wykonywanej przez aplikację podczas przebiegu profilowania. Zbieranie danych odbywa się przez zbieranie informacji o aplikacji w regularnych odstępach czasu lub częstotliwości próbkowania, takich jak wszystkie milisekundy, a następnie analizowanie tych danych w celu utworzenia modelu, w którym nastąpiło czas spędzony w aplikacji. Metoda próbkowania jest lekki i ma niewielki wpływ na wykonywanie profilowanej aplikacji. Narzędzia w profilerze wydajności korzystające z metody próbkowania obejmują narzędzie [użycie procesora CPU](../profiling/cpu-usage.md) .

## <a name="instrumentation"></a>Oprzyrządowanie

Profilowanie Instrumentacji zbiera szczegółowe informacje o pracy wykonywanej przez aplikację podczas przebiegu profilowania. Zbieranie danych odbywa się przez narzędzia, które umożliwiają wstrzyknięcie kodu do pliku binarnego, który przechwytuje informacje o chronometrażu lub przy użyciu punktów wywołania zwrotnego do zbierania i emitowania dokładnego czasu oraz informacji o liczbie wywołań podczas uruchamiania aplikacji. Metoda Instrumentacji ma duże obciążenie w porównaniu do podejścia opartego na próbkach. Narzędzia w profilerze wydajności korzystające z Instrumentacji obejmują narzędzie [alokacji obiektów platformy .NET](../profiling/dotnet-alloc-tool.md) .