---
title: Karta pamięć, okno dialogowe właściwości procesu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b70c5a982da866cbeb9e9907859ad4d270d79bd9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54772087"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Karta Pamięć, okno dialogowe właściwości procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj **pamięci** kartę, aby pokazać, jak korzysta z pamięci procesu. Aby wyświetlić [okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do [widok procesy](../debugger/processes-view.md) okna. Zaznacz dowolny węzeł procesu w drzewie, a następnie wybierz **właściwości** z **widoku** menu.  
  
 Następujące ustawienia są dostępne na **pamięci** karty:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Bajty wirtualne**|Bieżący rozmiar (w bajtach) wirtualnej przestrzeni adresowej używanej przez proces. Użycie wirtualnej przestrzeni adresowej nie musi oznaczać odpowiedniego użycia dysku lub stron pamięci głównej. Jednak pamięć wirtualna jest jednak ograniczona i przy użyciu zbyt dużo może ograniczyć możliwość ładowania bibliotek procesu.|  
|**Szczytowe Bajty wirtualne**|Maksymalna liczba bajtów w wirtualnej przestrzeni adresowej procesu został użyty w dowolnym momencie.|  
|**Zestaw roboczy**|Zestaw stron pamięci niedawno korzystały wątki w procesie. Jeśli ilość wolnej pamięci w komputerze jest powyżej wartości progowej, strony są pozostawiane w zestawie roboczym procesu, nawet jeśli nie są używane. Gdy ilość wolnej pamięci spada poniżej wartości progowej, strony są usuwane z zestawu roboczego. Jeśli są one potrzebne, będą one umieszczone w zestawie roboczym przed opuszczeniem pamięci głównej.|  
|**Szczytowy zestaw roboczy**|Maksymalna liczba stron w zestawu roboczego tego procesu w dowolnym momencie.|  
|**Bajty puli stronicowanej**|Bieżąca ilość puli stronicowanej proces został przydzielony. Pula stronicowana to obszar pamięci systemu, gdzie składniki systemu operacyjnego uzyskania miejsca realizowane wyznaczonych im zadań. Puli stronicowanej strony może być stronicowana się do pliku stronicowania, gdy nie ma dostępu systemu przez stałą czas.|  
|**Bajty puli niestronicowanej**|Bieżąca liczba bajtów w puli niestronicowanej przydzielonej przez proces. Puli niestronicowanej jest obszar pamięci systemu, gdzie miejsca są uzyskiwane przez składniki systemu operacyjnego, zgodnie z ich wykonywanie wyznaczonych im zadań. Strony puli niestronicowanej, nie stronicowany do pliku stronicowania; te pozostaną w pamięci głównej, tak długo, jak są przydzielone.|  
|**Bajty prywatne**|Bieżąca liczba bajtów, jaką przydzieliła tego procesu, które nie mogą być udostępniane innym procesom.|  
|**Bajty wolne**|Łączna liczba nieużywanych wirtualnej przestrzeni adresowej tego procesu.|  
|**Bajty zarezerwowane**|Całkowita ilość pamięci wirtualnej zarezerwowane do użytku w przyszłości przez ten proces.|  
|**Wolne bajty obrazu**|Ilość miejsca na wirtualny adres, który nie jest używany lub zastrzeżony przez obrazów w ramach tego procesu.|  
|**Zarezerwowane bajty obrazu**|Suma wszystkich pamięci wirtualnej zarezerwowane przez obrazy uruchomione w ramach tego procesu.|
