---
title: Widok procesu — dane rywalizacji o zasoby | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46bd3506744d37d3f203215cd9c152cef20142f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776684"
---
# <a name="process-view---contention-data"></a>Widok procesu — dane rywalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok procesu przedstawia dane rywalizacji o zasoby dotyczące procesów i wątków, które zostały wykonane podczas uruchomienia profilowania.  
  
 Po symbole są dostępne, procesy są wyświetlane według nazwy. Gdy symbole nie są dostępne, procesy są wyświetlane według ich adres pamięci, w formacie szesnastkowym. Wątki są wyświetlane jako elementy podrzędne procesu, który je utworzył.  
  
 W poniższej tabeli przedstawiono wartości kolumn w tabeli widoku proces.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Czas rozpoczęcia**|Liczba milisekund, czyli cykli procesora od rozpoczęcia profilowania do początku proces lub wątek.|  
|**Czas blokowania**|Całkowity czas, w którym funkcje proces lub wątek został zablokowany wykonywania.|  
|**% Czasu blokowania**|Wartość procentowa okresu istnienia proces lub wątek, w którym funkcje proces lub wątek został zablokowany wykonywania.|  
|**Rywalizacje**|Liczba prób wykonania funkcji proces lub wątek został zablokowany.|  
|**% Rywalizacji**|Wartość procentowa wszystkie rywalizacje w uruchomienia profilowania były rywalizacji procesów lub wątków.|  
|**Godzina zakończenia**|Liczba milisekund, czyli cykli procesora od czasu rozpoczęcia profilowania do końca proces lub wątek.|  
|**ID**|Wygenerowana przez system identyfikator proces lub wątek.|  
|**Okres istnienia**|Liczba milisekund, czyli cykli procesora od początku proces lub wątek do końca proces lub wątek lub końca okresu profilowania.|  
|**Typ**|Typ wiersza, przetwarzania lub wątku.<br /><br /> Tylko w **VSReport** raporty wiersza polecenia. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nazwa**|Nazwa proces lub wątek.|  
|**Unikatowy identyfikator**|Identyfikator wygenerowany przez program profilujący jest unikatowy dla proces lub wątek.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok procesu](../profiling/process-view.md)



