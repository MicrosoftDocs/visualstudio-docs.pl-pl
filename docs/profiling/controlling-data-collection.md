---
title: Kontrolowanie zbierania danych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 250ec5623a02f962a0d56d7f469ed37afee097ab
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630330"
---
# <a name="control-data-collection"></a>Sterowanie zbieraniem danych
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Narzędzia profilowania umożliwiają kontroli po danych profilowania zbieranych podczas sesji wydajności i określić funkcje, które są profilowane. W tej sekcji opisano sposób uruchamiają i zatrzymują zbieranie danych z **Eksplorator wydajności** i **kontroli zbierania danych** systemu windows oraz sposób ograniczyć liczbę obiektów, dla których są zbierane dane profilowania.

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Rozpoczęcie i zatrzymanie profilowania:** Można uruchomić do profilu aplikacji podczas uruchamiania aplikacji, lub można dołączyć profiler do procesu, który jest już uruchomiony. Gdy uruchomiona jest aplikacja docelowa, można wstrzymywać i wznawiać zbieranie danych. Możesz zakończyć sesję profilowania, zamknij aplikację docelową lub odłączenia profilera z uruchomionego procesu.|-   [Jak: Rozpoczęcia i zakończenia zbierania danych o wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Jak: Dołączanie i odłączanie narzędzi wydajności do uruchomionego procesu](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Jak: Wstrzymywanie i wznawianie zbierania danych o wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Skonfiguruj profilowania, aby ograniczyć ilość zebranych danych Instrumentacji:** Aby ograniczyć dane, które są zbierane w profilowania, które używają metody instrumentacji, można użyć właściwości konfiguracji sesji wydajności. Można uwzględnić lub wykluczyć pliki z rozszerzeniem dll określonych, przestrzenie nazw, klasy i funkcje. Można również wykluczyć funkcje, które nie spełniają próg rozmiaru, który określisz.|-   [Jak: Ograniczenie Instrumentacji do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Jak: Ograniczenie Instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Jak: Wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|

## <a name="related-sections"></a>Sekcje pokrewne
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Zobacz także
- [Eksplorator wydajności](../profiling/performance-explorer.md)