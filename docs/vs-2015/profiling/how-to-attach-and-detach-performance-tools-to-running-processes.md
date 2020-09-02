---
title: 'Instrukcje: dołączanie i odłączanie narzędzi wydajności do uruchomionych procesów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b8fc664ee47cd34ab984d1ac448b45c2f17c5b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64804963"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Instrukcje: dołączanie i odłączanie narzędzi wydajności do uruchomionych procesów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profiler może służyć do dołączania lub odłączania uruchomionego procesu, aby ułatwić próbkowanie i gromadzenie danych wydajności. Ta metoda służy do profilowania procesu, gdy chcesz uniknąć zbierania danych o czasie ładowania aplikacji lub monitorowania wydajności procesu po osiągnięciu określonego stanu.  
  
> [!NOTE]
> Poniższe kroki mają zastosowanie do dołączania i odłączania procesów z poziomu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] zintegrowanego environmnent programistycznego (IDE). Aby uzyskać informacje o sposobach korzystania z narzędzi wiersza polecenia, zobacz [profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md). Aby uzyskać informacje na temat sposobu profilowania usług, zobacz [profilowanie usług](../profiling/command-line-profiling-of-services.md).  
  
 Procesy dostępne do profilowania zależą od uprawnień dostępu użytkowników ustawionych przez administratora komputera. Konto użytkownika może na przykład mieć uprawnienia do następujących elementów:  
  
- Zaawansowane funkcje profilowania, gdy administrator ustawił sterownik i usługę do uruchomienia.  
  
- Przykładowe profilowania (Użytkownicy domeny).  
  
- Odmowa dostępu do profilowania do każdego.  
  
  Aby uzyskać więcej informacji, zobacz [profilowanie i zabezpieczenia systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md) oraz opcje administratora w programie [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Aby dołączyć do uruchomionego procesu  
  
1. W menu **Analizuj** wskaż polecenie **Profiler** , a następnie kliknij pozycję **Dołącz/Odłącz**.  
  
     \- oraz  
  
     W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij pozycję **Dołącz/Odłącz**.  
  
     Zostanie wyświetlone okno dialogowe **Dołącz profiler do procesu** .  
  
2. Kliknij nazwę procesu, do którego chcesz dołączyć.  
  
3. Kliknij przycisk **Dołącz**.  
  
### <a name="to-detach-from-a-running-process"></a>Aby odłączyć od uruchomionego procesu  
  
1. W menu **Analizuj** wskaż polecenie **Profiler** , a następnie kliknij pozycję **Dołącz/Odłącz**.  
  
     \- oraz  
  
     W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij pozycję **Dołącz/Odłącz**.  
  
     Zostanie wyświetlone okno dialogowe **Dołącz profiler do procesu** .  
  
2. Kliknij nazwę obrazu, z którego chcesz odłączyć.  
  
3. Kliknij przycisk **Odłącz**.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Przegląd sesji wydajności](../profiling/performance-session-overview.md)   
 [Instrukcje: uruchamianie i kończenie zbierania danych wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilowanie i zabezpieczenia systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)
