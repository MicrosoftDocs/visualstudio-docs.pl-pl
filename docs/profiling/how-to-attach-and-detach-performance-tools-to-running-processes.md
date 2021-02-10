---
title: Dołączanie narzędzi wydajności do uruchomionych procesów
description: Dowiedz się, jak użyć profilera programu Visual Studio do dołączenia do uruchomionego procesu lub odłączenia go, aby ułatwić pobieranie próbek i gromadzenie danych o wydajności.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 13323a768b9f42e70df9e8be6e64c9dd98438865
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958963"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Instrukcje: dołączanie narzędzi do oceny wydajności do uruchomionych procesów i ich odłączanie
Profiler może służyć do dołączania lub odłączania uruchomionego procesu, aby ułatwić próbkowanie i gromadzenie danych wydajności. Ta metoda służy do profilowania procesu, gdy chcesz uniknąć zbierania danych o czasie ładowania aplikacji lub monitorowania wydajności procesu po osiągnięciu określonego stanu.

> [!NOTE]
> Poniższe kroki mają zastosowanie do dołączania i odłączania procesów z poziomu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] zintegrowanego environmnent programistycznego (IDE). Informacje o sposobach korzystania z narzędzi wiersza polecenia znajdują się w temacie [profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md). Aby uzyskać informacje na temat sposobu profilowania usług, zobacz [Profiling Services](../profiling/command-line-profiling-of-services.md).

 Procesy dostępne do profilowania zależą od uprawnień dostępu użytkowników ustawionych przez administratora komputera. Konto użytkownika może na przykład mieć uprawnienia do następujących elementów:

- Zaawansowane funkcje profilowania, gdy administrator ustawił sterownik i usługę do uruchomienia.

- Przykładowe profilowania (Użytkownicy domeny).

- Odmowa dostępu do profilowania do każdego.

  Aby uzyskać więcej informacji, zobacz [profilowanie i zabezpieczenia systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md) oraz opcje administratora w programie [VSPerfCmd](../profiling/vsperfcmd.md).

### <a name="to-attach-to-a-running-process"></a>Aby dołączyć do uruchomionego procesu

1. W menu **debugowanie** wskaż polecenie **Profiler**, a następnie **Eksplorator wydajności**, a następnie kliknij pozycję **Dołącz**.

     Zostanie wyświetlone okno dialogowe **Dołącz profiler do procesu** .

2. Kliknij nazwę procesu, do którego chcesz dołączyć.

3. Kliknij przycisk **Dołącz**.

### <a name="to-detach-from-a-running-process"></a>Aby odłączyć od uruchomionego procesu

1. w menu **Debuguj** wskaż polecenie **Profiler**, a następnie **Eksplorator wydajności**, a następnie kliknij polecenie **Odłącz**.

     Zostanie wyświetlone okno dialogowe **Dołącz profiler do procesu** .

2. Kliknij nazwę obrazu, z którego chcesz odłączyć.

3. Kliknij przycisk **Odłącz**.

## <a name="see-also"></a>Zobacz też
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)
- [Sesja wydajności — omówienie](../profiling/performance-session-overview.md)
- [Instrukcje: uruchamianie i kończenie zbierania danych wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Profilowanie i bezpieczeństwo systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
