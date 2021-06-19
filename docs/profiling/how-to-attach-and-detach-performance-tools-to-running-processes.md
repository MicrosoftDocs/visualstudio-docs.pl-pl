---
title: Dołączanie narzędzi do wydajności do uruchomionych procesów
description: Dowiedz się, jak używać Visual Studio profilera, aby dołączać do uruchomionego procesu lub odłączyć go od uruchomionego procesu, aby ułatwić próbkowanie i zbieranie danych wydajności.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4002334d8fba7b31e33eecd5cf49532ba384046d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390024"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Instrukcje: dołączanie narzędzi do oceny wydajności do uruchomionych procesów i ich odłączanie
Profiler może służyć do dołączania do uruchomionego procesu lub odłączania go od uruchomionego procesu w celu ułatwienia próbkowania i zbierania danych wydajności. Tej metody można użyć do profilowania procesu, gdy chcesz uniknąć zbierania danych dotyczących czasu ładowania aplikacji lub monitorowania wydajności procesu po osiągnięciu określonego stanu.

> [!NOTE]
> Poniższe kroki dotyczą dołączania i odłączania procesów ze zintegrowanego środowiska projektowego [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] (IDE). Aby uzyskać informacje na temat używania narzędzi wiersza polecenia, zobacz [Profile (Profil) z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md). Aby uzyskać informacje na temat sposobu profilowania usług, zobacz [Profile services](../profiling/command-line-profiling-of-services.md).

 Procesy dostępne do profilowania zależą od uprawnień dostępu użytkowników ustawionych przez administratora komputera. Konto użytkownika może mieć na przykład uprawnienia do następujących czynności:

- Zaawansowane funkcje profilowania, gdy administrator ustawił sterownik i usługę na uruchamianie.

- Tylko profilowanie przykładowe (użytkownicy domeny).

- Odmowa dostępu do profilowania wszystkim.

  Aby uzyskać więcej informacji, zobacz [Profilowanie i zabezpieczenia systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md) oraz opcje ADMINISTRATORA w [narzędziu VSPerfCmd.](../profiling/vsperfcmd.md)

### <a name="to-attach-to-a-running-process"></a>Aby dołączyć do uruchomionego procesu

1. W menu **Debug (Debugowanie)** wskaż pozycję **Profiler**, a następnie wybierz **Eksplorator wydajności**, a następnie kliknij pozycję Attach **(Dołącz).**

     Zostanie **wyświetlone okno dialogowe Dołączanie profilera** do procesu.

2. Kliknij nazwę procesu, do którego chcesz dołączyć.

3. Kliknij pozycję **Attach (Dołącz).**

### <a name="to-detach-from-a-running-process"></a>Aby odłączyć się od uruchomionego procesu

1. w menu **Debugowanie** wskaż pozycję **Profiler,** a następnie wybierz **Eksplorator wydajności**, a następnie kliknij pozycję **Odłącz.**

     Zostanie **wyświetlone okno dialogowe Dołączanie profilera** do procesu.

2. Kliknij nazwę obrazu, od którego chcesz odłączyć.

3. Kliknij pozycję **Odłącz.**

## <a name="see-also"></a>Zobacz też
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)
- [Sesja wydajności — omówienie](../profiling/performance-session-overview.md)
- [Jak rozpocząć i zakończyć zbieranie danych wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Profilowanie i bezpieczeństwo systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
