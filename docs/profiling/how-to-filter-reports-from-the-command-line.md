---
title: 'Instrukcje: filtrowanie raportów z wiersza polecenia | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bd6462f9159a2926c6dfa45dcadff860cce9ca1
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778937"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Instrukcje: filtrowanie raportów z wiersza polecenia
Za pomocą opcji polecenia **VSPerfReport** można filtrować raporty do określonego segmentu czasu pliku danych profilowania lub ograniczać dane do jednego lub kilku procesów lub wątków. Aby uzyskać więcej informacji na temat tego polecenia, zobacz [VSPerfReport](../profiling/vsperfreport.md).

|Opcje|Opis|
|-------------|-----------------|
|**StartTime:** [*Value*]|Pokaż tylko dane zebrane po wartości (w milisekundach).|
|**Endtime:** [*wartość*]|Pokaż tylko dane zebrane przed wartością (w milisekundach).|
|**FilterFile:** `VSPFFile`|Określa lokalizację pliku filtru, który został wygenerowany z okna **raportu wydajności programu Visual Studio** .|
|**MsFilter:** [*StartTime, Duration*]|Pokaż tylko dane z `StartTime` aż do `Duration` Długość (w milisekundach).|
|**Proces:** [*PID*]|Wyświetla tylko dane z określonego procesu.|
|**Wątek:** [*ThreadID*]|Wyświetla tylko dane z określonego wątku.|
|**Wątek:** [*ThreadID, identyfikator procesu*]|Wyświetla tylko dane z określonego wątku, które są skojarzone z określonym procesem.|
