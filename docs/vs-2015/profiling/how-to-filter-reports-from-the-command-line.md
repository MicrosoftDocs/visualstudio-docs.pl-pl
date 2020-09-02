---
title: 'Instrukcje: filtrowanie raportów z wiersza polecenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db2c9d845af962fc17da1ebd84e8dd5fe6ffadab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146003"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Porady: filtrowanie raportów z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
