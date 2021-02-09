---
title: Filtrowanie raportów z wiersza polecenia | Microsoft Docs
description: Użyj VSPerfReport.exe, aby ograniczyć raportowanie do określonego okresu lub do wybranych procesów i wątków. W tym artykule wymieniono opcje z opisami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dda6b89dcdfacc286417924c666b3ebd805f1cc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897721"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Instrukcje: filtrowanie raportów z poziomu wiersza polecenia
Za pomocą opcji polecenia **VSPerfReport** można filtrować raporty do określonego segmentu czasu pliku danych profilowania lub ograniczać dane do jednego lub kilku procesów lub wątków. Aby uzyskać więcej informacji na temat tego polecenia, zobacz [VSPerfReport](../profiling/vsperfreport.md).

|Opcje|Opis|
|-------------|-----------------|
|**StartTime:**[*Value*]|Pokaż tylko dane zebrane po wartości (w milisekundach).|
|**Endtime:**[*wartość*]|Pokaż tylko dane zebrane przed wartością (w milisekundach).|
|**FilterFile:**`VSPFFile`|Określa lokalizację pliku filtru, który został wygenerowany z okna **raportu wydajności programu Visual Studio** .|
|**MsFilter:**[*StartTime, Duration*]|Pokaż tylko dane z `StartTime` do długości `Duration` (w milisekundach).|
|**Proces:**[*PID*]|Wyświetla tylko dane z określonego procesu.|
|**Wątek:**[*ThreadID*]|Wyświetla tylko dane z określonego wątku.|
|**Wątek:**[*ThreadID, identyfikator procesu*]|Wyświetla tylko dane z określonego wątku, które są skojarzone z określonym procesem.|
