---
title: Widok procesu — dane rywalizacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e43541ddb75b067faa23437d315ce5f239256b1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180232"
---
# <a name="process-view---contention-data"></a>Widok procesu — dane rywalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok procesu przedstawia dane rywalizacji dotyczące procesów i wątków, które zostały wykonane podczas przebiegu profilowania.  
  
 Gdy symbole są dostępne, procesy są wyświetlane według nazwy. Gdy symbole nie są dostępne, procesy są wyświetlane według adresów pamięci w formacie szesnastkowym. Wątki są wyświetlane jako elementy podrzędne procesu, który go utworzył.  
  
 W poniższej tabeli objaśniono wartości kolumn w tabeli widoku procesu.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Godzina rozpoczęcia**|Liczba milisekund lub cykli procesora od początku profilowania do początku procesu lub wątku.|  
|**Czas blokowania**|Łączny czas, w którym funkcje procesu lub wątku zostały zablokowane do wykonania.|  
|**% Czasu blokowania**|Wartość procentowa okresu istnienia procesu lub wątku, w którym zablokowano wykonywanie funkcji przez proces lub wątek.|  
|**Rywalizacji**|Liczba operacji blokowania wykonywania funkcji przez proces lub wątek.|  
|**Rywalizacji**|Wartość procentowa wszystkich rywalizacji w przebiegu profilowania, które były rywalizacjami o proces lub wątek.|  
|**Czas zakończenia**|Liczba milisekund lub cykli procesora od początku profilowania do końca procesu lub wątku.|  
|**ID**|Wygenerowany przez system identyfikator procesu lub wątku.|  
|**Czas życia**|Liczba milisekund lub cykli procesora od początku procesu lub wątku do końca procesu lub wątku albo końca profilowania.|  
|**Typ**|Typ wiersza, proces lub wątek.<br /><br /> Tylko w raportach wiersza polecenia **VSReport** . Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nazwa**|Nazwa procesu lub wątku.|  
|**Unikatowy identyfikator**|Wygenerowany przez profiler identyfikator, który jest unikatowy dla procesu lub wątku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok procesu](../profiling/process-view.md)
