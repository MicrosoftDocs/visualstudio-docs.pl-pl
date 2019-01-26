---
title: 'Instrukcje: Filtrowanie raportów z poziomu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d55438c95bcb82306afde7c65c22f3f29b98578d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069229"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Instrukcje: Filtrowanie raportów z poziomu wiersza polecenia
Za pomocą opcji **VSPerfReport** polecenia, można filtrować raporty na segment określony czas w pliku danych profilowania lub ograniczyć je do procesów lub wątków. Aby uzyskać więcej informacji na temat tego polecenia, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**Godzina rozpoczęcia:**[*wartość*]|Wyświetla tylko dane zebrane po wartości (w milisekundach).|  
|**EndTime:**[*wartość*]|Wyświetla tylko dane zebrane przed wartością (w milisekundach).|  
|**FilterFile:** `VSPFFile`|Określa lokalizację pliku filtru, który został wygenerowany z **raport dotyczący wydajności programu Visual Studio** okna.|  
|**MsFilter:**[*godzina rozpoczęcia, czas trwania*]|Wyświetla tylko dane z `StartTime` aż do długości `Duration` (w milisekundach).|  
|**Proces:**[*Pid*]|Wyświetla tylko dane z określonego procesu.|  
|**Wątek:**[*ThreadID*]|Wyświetla tylko dane z określonego wątku.|  
|**Wątek:**[*Identyfikator_wątku, Identyfikator_procesu*]|Wyświetla tylko dane z określonego wątku, który jest skojarzony z określonym procesem.|