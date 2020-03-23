---
title: Raport śledzenia zdarzeń dla systemu Windows (ETW) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 19412d184377637c29f34b2fe3ffd033f176b97c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779301"
---
# <a name="event-tracing-for-windows-etw-report"></a>Raport Śledzenia zdarzeń dla systemu Windows (ETW)
Raport Śledzenia zdarzeń dla systemu Windows (ETW) zawiera listę zdarzeń ETW, które zostały zarejestrowane w sesji wydajności narzędzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowania. Dane ETW są zbierane w pliku binarnym (.* etl*).

> [!NOTE]
> Nie można wyświetlić [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] raportów ETW w interfejsie.

- Aby uzyskać informacje na temat zbierania ETW [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] za pomocą narzędzi profilowania z interfejsu, zobacz [Jak: Zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW).](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

- Aby uzyskać informacje dotyczące sposobu zbierania danych ETW przy użyciu narzędzi wiersza polecenia [VSPerfCmd,](../profiling/vsperfcmd.md) zobacz [Zdarzenia](../profiling/events-vsperfcmd.md).

- Raport ETW jest generowany przy użyciu polecenia **VSReport/Summary:ETW.** Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).

|Kolumna|Opis|
|------------|-----------------|
|**Sygnatura czasowa**|Określa, kiedy wystąpiło zdarzenie.|
|**Identyfikator procesu**|Identyfikuje proces, który wygenerował zdarzenie.|
|**Identyfikator wątku**|Identyfikuje wątek, który wygenerował zdarzenie.|
|**Opis**|Identyfikuje dostawcę zdarzeń.|
|**Typ**|Identyfikuje typ zdarzenia.|
|**Właściwości**|Właściwości zdarzenia. Każde zdarzenie jest parą oddzielaną przecinkami i wartością nazwy, która jest ujęta w nawiasy.|
