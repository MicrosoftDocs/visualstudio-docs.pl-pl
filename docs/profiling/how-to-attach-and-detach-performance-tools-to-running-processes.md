---
title: Dołączanie narzędzi wydajności do uruchomionych procesów
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4c4ae54d6b90166de31c338a5e606eaf31ecd6cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779171"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Instrukcje: dołączanie narzędzi do oceny wydajności do uruchomionych procesów i ich odłączanie
Profiler może służyć do dołączania lub odłączania od uruchomionego procesu, aby ułatwić próbkowanie i zbieranie danych o wydajności. Ta metoda służy do profilowania procesu, gdy chcesz uniknąć zbierania danych o czasie ładowania aplikacji lub do monitorowania wydajności procesu po osiągnięciu określonego stanu.

> [!NOTE]
> Poniższe kroki dotyczą dołączania i odłączania [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] procesów z poziomu zintegrowanego środowiska rozwoju (IDE). Aby uzyskać informacje dotyczące korzystania z narzędzi wiersza polecenia, zobacz [Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md). Aby uzyskać informacje dotyczące profilowania usług, zobacz [Usługi profilu](../profiling/command-line-profiling-of-services.md).

 Procesy dostępne dla profilu zależą od uprawnień dostępu użytkownika ustawionych przez administratora komputera. Konto Użytkownika może na przykład mieć uprawnienia do następujących czynności:

- Zaawansowane funkcje profilowania, gdy administrator ustawił sterownik i usługę do uruchomienia.

- Tylko przykładowe profilowanie (użytkownicy domeny).

- Odmów dostępu do profilowania wszystkim.

  Aby uzyskać więcej informacji, zobacz [Profilowanie i zabezpieczenia systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md) oraz opcje ADMIN w programie [VSPerfCmd](../profiling/vsperfcmd.md).

### <a name="to-attach-to-a-running-process"></a>Aby dołączyć do uruchomionego procesu

1. W menu **Debugowanie** wskaż polecenie **Profiler**, a następnie **Eksplorator wydajności**, a następnie kliknij przycisk **Dołącz**.

     Zostanie wyświetlone okno dialogowe **Dołączanie profilera do procesu.**

2. Kliknij nazwę procesu, do którego chcesz dołączyć.

3. Kliknij **pozycję Dołącz**.

### <a name="to-detach-from-a-running-process"></a>Aby odłączyć się od uruchomionego procesu

1. n menu **Debugowanie,** wskaż **polecenie Profiler,** następnie **Eksplorator wydajności**, a następnie kliknij przycisk **Odłącz**.

     Zostanie wyświetlone okno dialogowe **Dołączanie profilera do procesu.**

2. Kliknij nazwę obrazu, od której chcesz odłączyć.

3. Kliknij przycisk **Odłącz**.

## <a name="see-also"></a>Zobacz też
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)
- [Omówienie sesji skuteczności](../profiling/performance-session-overview.md)
- [Jak: Uruchamianie i kończy zbieranie danych o wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Profilowanie i bezpieczeństwo systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
