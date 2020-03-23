---
title: Kontrolowanie gromadzenia danych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 48c7047bdd321943074221c9f09193970d42a247
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777806"
---
# <a name="control-data-collection"></a>Sterowanie zbieraniem danych
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Narzędzia profilowania umożliwiają kontrolowanie, kiedy dane profilowania są zbierane podczas sesji wydajności i określanie funkcji, które są profilowane. W tej sekcji opisano sposób uruchamiania i zatrzymywania zbierania danych z okien **Eksploratora wydajności** i **kontroli zbierania danych** oraz jak ograniczyć obiekty, dla których zbierane są dane profilowania.

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Rozpocznij i zatrzymaj profilowanie:** Można rozpocząć profil aplikacji po uruchomieniu aplikacji lub można dołączyć profiler do procesu, który jest już uruchomiony. Gdy aplikacja docelowa jest uruchomiona, można wstrzymać i wznowić zbieranie danych. Zakończenie sesji profilowania przez zamknięcie aplikacji docelowej lub odłączenie profilera od uruchomionego procesu.|-   [Jak: Uruchamianie i kończy zbieranie danych o wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Jak: Dołączanie i odłączanie narzędzi wydajności do uruchomionych procesów](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Jak: Wstrzymanie i wznowienie zbierania danych o wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Skonfiguruj profilowanie instrumentacji, aby ograniczyć zebrane dane:** Właściwości konfiguracji sesji wydajności można użyć, aby ograniczyć dane, które są zbierane w profilowania uruchamia, które używają metody instrumentacji. Można dołączyć lub wykluczyć określone pliki dll, przestrzenie nazw, klasy i funkcje. Można również wykluczyć funkcje, które nie spełniają określonego progu rozmiaru.|-   [Jak: Ograniczanie oprzyrządowania do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Jak: Ograniczenie oprzyrządowania do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Jak: Wykluczyć lub uwzględnić krótkie funkcje z oprzyrządowania](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|

## <a name="related-sections"></a>Powiązane sekcje
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Zobacz też
- [Eksplorator wydajności](../profiling/performance-explorer.md)
