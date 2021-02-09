---
title: Kontrolowanie zbierania danych | Microsoft Docs
description: Dowiedz się, jak uruchamiać i zatrzymywać zbieranie danych narzędzia profilowania oraz jak ograniczyć obiekty, dla których zbierane są dane profilowania. Ten artykuł zawiera omówienie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1ca23b5477cee37154f1334328745a5d2b066b39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910732"
---
# <a name="control-data-collection"></a>Sterowanie zbieraniem danych
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Narzędzia profilowania umożliwiają kontrolę, kiedy dane profilowania są zbierane podczas sesji wydajności i określają funkcje, które są profilowane. W tej sekcji opisano sposób uruchamiania i zatrzymywania zbierania danych z okien **Eksplorator wydajności** i **kontroli zbierania danych** oraz sposobu ograniczania obiektów, dla których zbierane są dane profilowania.

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Uruchom i Zatrzymaj profilowanie:** Możesz rozpocząć Profilowanie aplikacji podczas uruchamiania aplikacji lub dołączyć Profiler do procesu, który jest już uruchomiony. Po uruchomieniu aplikacji docelowej można wstrzymywać i wznawiać zbieranie danych. Zakończenie sesji profilowania przez zamknięcie aplikacji docelowej lub odłączenie profilera od uruchomionego procesu.|-   [Instrukcje: uruchamianie i kończenie zbierania danych wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Instrukcje: dołączanie i odłączanie narzędzi wydajności do uruchomionych procesów](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Instrukcje: Wstrzymywanie i wznawianie zbierania danych wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Skonfiguruj profilowanie instrumentacji, aby ograniczyć liczbę zebranych danych:** Właściwości konfiguracji sesji wydajności można użyć do ograniczenia danych zbieranych w ramach uruchamiania profilowania, które korzystają z metody instrumentacji. Można dołączać lub wykluczać określone pliki. dll, przestrzenie nazw, klasy i funkcje. Można również wykluczyć funkcje, które nie spełniają określonego progu rozmiaru.|-   [Instrukcje: ograniczanie instrumentacji do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Instrukcje: ograniczanie instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Instrukcje: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|

## <a name="related-sections"></a>Sekcje pokrewne
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Zobacz też
- [Eksplorator wydajności](../profiling/performance-explorer.md)
