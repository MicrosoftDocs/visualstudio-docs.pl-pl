---
title: 'Porady: filtrowanie raportów z poziomu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb8df34291d99d093ccf0d053d5dd1fbe2955232
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789788"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Porady: filtrowanie raportów z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



