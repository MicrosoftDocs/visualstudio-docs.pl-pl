---
title: 'Jak: Filtrowanie raportów z wiersza polecenia | Dokumenty firmy Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778937"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Instrukcje: filtrowanie raportów z poziomu wiersza polecenia
Za pomocą opcji **dla polecenia VSPerfReport,** można filtrować raporty do określonego segmentu czasu pliku danych profilowania lub ograniczyć dane do jednego lub więcej procesów lub wątków. Aby uzyskać więcej informacji na temat tego polecenia, zobacz [VSPerfReport](../profiling/vsperfreport.md).

|Opcje|Opis|
|-------------|-----------------|
|**Czas rozpoczęcia:**[*Wartość*]|Pokaż tylko dane zebrane po wartości (w milisekundach).|
|**Czas zakończenia:**[*Wartość*]|Pokaż tylko dane zebrane przed wartością (w milisekundach).|
|**Plik filtra:**`VSPFFile`|Określa lokalizację pliku filtru wygenerowanego z okna **Raport wydajności programu Visual Studio.**|
|**MsFilter:**[*Czas trwania startu*]|Dane są `StartTime` wyświetlane tylko `Duration` od momentu (w milisekundach).|
|**Proces:**[*Pid*]|Pokaż tylko dane z określonego procesu.|
|**Wątek:**[*ThreadID*]|Pokaż tylko dane z określonego wątku.|
|**Wątek:**[*ThreadID,ProcessID*]|Pokaż tylko dane z określonego wątku, który jest skojarzony z określonym procesem.|
