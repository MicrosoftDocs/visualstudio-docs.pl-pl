---
title: Filtrowanie raportów z wiersza polecenia | Microsoft Docs
description: Użyj VSPerfReport.exe, aby ograniczyć raportowanie do określonego okresu lub do wybranych procesów i wątków. W tym artykule wymieniono opcje z opisami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 968b02569c123326710482705146844ef393dfa6
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801200"
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
