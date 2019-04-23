---
title: Śledzenie zdarzeń systemu Windows (ETW) raport | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bfcb10bdbbfcb8e4b98f8d90d6652832059107d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108220"
---
# <a name="event-tracing-for-windows-etw-report"></a>Zdarzenia śledzenia dla systemu Windows (ETW) — Raport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Raport śledzenie zdarzeń dla Windows (ETW) zawiera listę zdarzeń ETW, które zostały zapisane w sesji pomiaru wydajności [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools. Dane ETW są zbierane w pliku danych binarnych (ETL).  
  
> [!NOTE]
>  Nie można wyświetlić raporty ETW w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu.  
  
- Aby uzyskać informacje dotyczące zbierania zdarzeń systemu Windows przy użyciu narzędzi profilowania z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu, zobacz [jak: Zbieranie zdarzeń śledzenia for Windows (ETW) — dane](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Aby uzyskać informacje dotyczące zbierania danych ETW przy użyciu [VSPerfCmd](../profiling/vsperfcmd.md) narzędzi wiersza polecenia, zobacz [zdarzenia](../profiling/events-vsperfcmd.md).  
  
- Generowanie raportu ETW za pomocą **VSReport / Summary: ETW** polecenia. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Znacznik czasu:**|Umożliwia określenie, kiedy wystąpiło zdarzenie.|  
|**Identyfikator procesu**|Identyfikuje proces, który wygenerował zdarzenie.|  
|**Identyfikator wątku**|Identyfikuje wątku, który wygenerował zdarzenie.|  
|**Opis**|Określa dostawcę zdarzeń.|  
|**Typ**|Określa typ zdarzenia.|  
|**Właściwości**|Właściwości zdarzenia. Każde wydarzenie jest parą rozdzielonych przecinkami, nazwa wartość, która jest ujęty w nawiasy kwadratowe.|
