---
title: Analizowanie wydajności kodu asynchronicznego .NET | Microsoft Docs
description: Użyj narzędzia asynchronicznego platformy .NET do analizowania wydajności kodu asynchronicznego. Dla każdego wymienionego zadania istnieje chronometraż. Aby wyświetlić kod, użyj polecenie Przejdź do pliku źródłowego.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 86575cd71c41ac8ac874e9b62f8273ee46e02c57
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205492"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>Analizowanie wydajności kodu asynchronicznego .NET

Użyj narzędzia asynchronicznego platformy .NET do analizowania wydajności kodu asynchronicznego w aplikacji.

> [!NOTE]
> Narzędzie asynchroniczne platformy .NET wymaga programu Visual Studio 2019 w wersji 16,7 lub nowszej oraz projektu .NET, który używa **Async** i **await**.

## <a name="setup"></a>Konfigurowanie

1. Wybierz **kombinację klawiszy Alt + F2** , aby otworzyć Profiler wydajności w programie Visual Studio.

1. Zaznacz pole wyboru **Async dla platformy .NET** .

   ![Wybrane narzędzie asynchroniczne platformy .NET](../profiling/media/async-tool-selected.png "Wybrane narzędzie asynchroniczne platformy .NET")

1. Kliknij przycisk **Uruchom** , aby uruchomić narzędzie.

1. Po uruchomieniu narzędzia Przejdź do scenariusza, który chcesz profilować w aplikacji. Następnie wybierz pozycję **Zatrzymaj zbieranie** lub Zamknij aplikację, aby zobaczyć swoje dane.

1. Po zatrzymaniu kolekcji zostanie wyświetlona tabela działań, które wystąpiły podczas sesji profilowania.

   ![Zatrzymano narzędzie asynchroniczne platformy .NET](../profiling/media/async-tool-opened.png "Zatrzymano narzędzie asynchroniczne platformy .NET")

Zdarzenia asynchroniczne są zorganizowane w działania chronologicznie. Każda z nich Wyświetla godzinę rozpoczęcia, godzinę zakończenia i czas trwania.

Każdy wiersz, który odnosi się do [zadania](/dotnet/api/system.threading.tasks) , ma etykietę w kolumnie **Nazwa** . Dla każdej nazwy zadania, której nie można rozpoznać, pojawi się **zadanie w** etykiecie. Następuje nazwa metody, w której odbywa się zadanie. Jeśli działanie asynchroniczne nie zostanie ukończone w ramach sesji zbierania, w kolumnie **czas zakończenia** zostanie wyświetlona **niepełna** etykieta.

Aby dokładniej zbadać określone zadanie lub działanie, kliknij prawym przyciskiem myszy wiersz. Następnie wybierz pozycję **Przejdź do pliku źródłowego** , aby zobaczyć, gdzie nastąpiło działanie w kodzie.

![Narzędzie asynchroniczne platformy .NET z wybraną opcją przejdź do pliku źródłowego](../profiling/media/async-tool-gotosource.png "Narzędzie asynchroniczne platformy .NET z wybraną opcją przejdź do pliku źródłowego")

## <a name="see-also"></a>Zobacz też

- [Optymalizowanie ustawień profilera](../profiling/optimize-profiler-settings.md)