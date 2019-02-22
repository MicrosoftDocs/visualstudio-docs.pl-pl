---
title: Dołącz narzędzia do oceny wydajności do uruchomionego procesu
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
ms.workload:
- multiple
ms.openlocfilehash: f56121354e9c6e508ab591d306f7e210f6963694
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603587"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Instrukcje: Dołączanie narzędzi do oceny wydajności do uruchomionych procesów i ich odłączanie
Program profilujący może służyć do dołączenia do lub odłączyć od uruchomionego procesu, aby ułatwić pobierania próbek i zbieranie danych wydajności. Ta metoda umożliwia profilować proces w przypadku, gdy chcesz uniknąć zbierania danych o czas ładowania aplikacji lub do monitorowania wydajności procesu po nim osiągnie określony stan.

> [!NOTE]
>  Poniższe kroki dotyczą Dołączanie i odłączanie procesów z poziomu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] zintegrowane environmnent programowania (IDE). Aby uzyskać informacje o tym, jak używać narzędzi wiersza polecenia, zobacz [profilu z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md). Aby uzyskać informacji dotyczących usług profilu, zobacz [profilu usługi](../profiling/command-line-profiling-of-services.md).

 Procesy, które są dostępne dla profilu zależą od uprawnień dostępu użytkowników, które są ustawiane przez administratora komputera. Konto użytkownika może na przykład mają uprawnienie do żadnego z następujących czynności:

- Zaawansowane funkcje, profilowania, gdy administrator ustawił sterownik i uruchomienie usługi.

- Przykład profilowanie tylko (użytkowników domeny).

- Odmowa dostępu do profilowania, aby wszyscy.

  Aby uzyskać więcej informacji, zobacz [zabezpieczeń profilowania i Windows Vista](../profiling/profiling-and-windows-vista-security.md) i opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).

### <a name="to-attach-to-a-running-process"></a>Aby dołączyć do uruchomionego procesu

1.  Na **debugowania** menu wskaż **Profiler**, następnie **Eksplorator wydajności**, a następnie kliknij przycisk **Dołącz**.

     **Dołączyć Profiler do procesu** pojawi się okno dialogowe.

2.  Kliknij nazwę, którą chcesz dołączyć do procesu.

3.  Kliknij przycisk **dołączyć**.

### <a name="to-detach-from-a-running-process"></a>Można odłączyć od uruchomionego procesu

1.  n **debugowania** menu wskaż **Profiler**, następnie **Eksplorator wydajności**, a następnie kliknij przycisk **Odłącz**.

     **Dołączyć Profiler do procesu** pojawi się okno dialogowe.

2.  Kliknij nazwę obrazu, z którego chcesz odłączyć.

3.  Kliknij przycisk **odłączyć**.

## <a name="see-also"></a>Zobacz także
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)
- [Sesja wydajności — omówienie](../profiling/performance-session-overview.md)
- [Instrukcje: Rozpoczęcia i zakończenia zbierania danych o wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Profilowanie i bezpieczeństwo systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)