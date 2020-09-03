---
title: Karta Ogólne, okno dialogowe właściwości procesu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9256ca4141e9e4ec9e5ae218f1e5a11bf2fa5362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182282"
---
# <a name="general-tab-process-properties-dialog-box"></a>Karta ogólna, okno dialogowe właściwości procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Skorzystaj z karty **Ogólne** , aby dowiedzieć się więcej o określonym procesie. Aby wyświetlić okno [dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do okna [widok procesów](../debugger/processes-view.md) . Wybierz dowolny węzeł procesu w drzewie, a następnie wybierz polecenie **Właściwości** z menu **Widok** .  
  
 Na karcie **Ogólne** dostępne są następujące ustawienia:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Nazwa modułu**|Nazwa modułu.|  
|**Identyfikator procesu**|Unikatowy identyfikator tego procesu. Numery identyfikatorów procesów są ponownie używane, aby identyfikować proces tylko w okresie istnienia tego procesu. Typ obiektu procesu jest tworzony podczas uruchamiania programu. Wszystkie wątki w procesie mają tę samą przestrzeń adresową i mają dostęp do tych samych danych.|  
|**Priorytet podstawowy**|Bieżący Priorytet podstawowy tego procesu. Wątki w ramach procesu mogą podnieść i obniżyć własny priorytet podstawowy względem priorytetu podstawowego procesu.|  
|**Wątki**|Liczba wątków aktywnych obecnie w tym procesie.|  
|**Czas procesora CPU**|Łączny czas procesora CPU poświęcony na ten proces i jego wątki. Równy czasowi użytkownika plus czas uprzywilejowany.|  
|**Czas użytkownika**|Łączny czas, który upłynął, gdy wątki tego procesu poświęcają na wykonywanie kodu w trybie użytkownika w wątkach, które nie są bezczynne. Aplikacje są wykonywane w trybie użytkownika, tak jak w przypadku podsystemów, takich jak Menedżer okien i aparat grafiki.|  
|**Uprzywilejowany czas**|Łączny czas, który upłynął w trybie uprzywilejowanym w nieczynnych wątkach. Warstwa usług, procedury wykonawcze i wykonywanie jądra w trybie uprzywilejowanym. Sterowniki urządzeń dla większości urządzeń oprócz kart graficznych i drukarek są również wykonywane w trybie uprzywilejowanym. Niektóre zadania, które system Windows dla aplikacji mogą pojawić się w innych procesach podsystemu, oprócz uprzywilejowanego czasu.|  
|**Czas, który upłynął**|Łączny czas, który upłynął, gdy ten proces został uruchomiony.|
