---
title: Śledzenie zdarzeń systemu Windows (ETW) raport | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e732d8350949d8ac9bfdc6a89c87b6d415fc726
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913268"
---
# <a name="event-tracing-for-windows-etw-report"></a>Raport o zdarzeniach śledzenie Windows (ETW)
Raport śledzenie zdarzeń dla Windows (ETW) zawiera listę zdarzeń ETW, które zostały zapisane w sesji pomiaru wydajności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools. Dane funkcji ETW są zbierane w pliku binarnym (. *etl*) pliku.  
  
> [!NOTE]
>  Nie można wyświetlić raporty ETW w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu.  
  
- Aby uzyskać informacje dotyczące zbierania zdarzeń systemu Windows przy użyciu narzędzi profilowania z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu, zobacz [jak: Zbieraj dane zdarzenia śledzenia dla Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
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