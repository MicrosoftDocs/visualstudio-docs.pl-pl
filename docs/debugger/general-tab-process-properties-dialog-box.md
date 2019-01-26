---
title: Karta Ogólne, okno dialogowe właściwości procesu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41667abc250bc2b2ffc869b714fafbcae8f21297
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931963"
---
# <a name="general-tab-process-properties-dialog-box"></a>Karta ogólna, okno dialogowe właściwości procesu
Użyj **ogólne** kartę, aby dowiedzieć się więcej na temat określonego procesu. Aby wyświetlić [okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do [widok procesy](../debugger/processes-view.md) okna. Zaznacz dowolny węzeł procesu w drzewie, a następnie wybierz **właściwości** z **widoku** menu.  
  
 Następujące ustawienia są dostępne na **ogólne** karty:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Nazwa modułu**|Nazwa modułu.|  
|**Identyfikator procesu**|Unikatowy identyfikator tego procesu. Numery identyfikatorów procesów są używane ponownie, więc identyfikują one proces tylko w przypadku istnienia tego procesu. Typ obiektu procesu jest tworzony po uruchomieniu programu. Wszystkie wątki w procesie udostępnianie tej samej przestrzeni adresowej i mieć dostęp do tych samych danych.|  
|**Priorytet podstawowy**|Bieżący priorytet bazowy tego procesu. Wątki w procesie można podnieść i Obniż swoje własne podstawowy priorytet względem priorytet podstawowy.|  
|**Wątki**|Liczba aktywnych wątków w tym procesie.|  
|**Czas procesora CPU**|Łączny czas Procesora poświęcony ten proces i wątków. Taki sam jak czas użytkownika, a także czas uprzywilejowany.|  
|**Czas użytkownika**|Skumulowany czas, który upłynął, wątki tego procesu ma poświęcony na wykonywanie kodu w trybie użytkownika-wątki. Aplikacje są wykonywane w trybie użytkownika, tak jak podsystemy, takie jak Menedżer okien i aparat grafiki.|  
|**Czas uprzywilejowany**|Całkowity czas ten proces jest uruchomiony w trybie uprzywilejowanym-wątki. Warstwy usług, procedury wykonawczy i jądra należy wykonać w trybie uprzywilejowanym. Sterowniki urządzeń dla większości urządzeń innych niż kart graficznych i drukarki również wykonać w trybie uprzywilejowanym. Pewnej pracy, który Windows wykonuje aplikacji mogą zostać wyświetlone inne procesy podsystemu, oprócz czasu uprzywilejowanego.|  
|**Czas, który upłynął**|Całkowity czas wykonywania tego procesu.|