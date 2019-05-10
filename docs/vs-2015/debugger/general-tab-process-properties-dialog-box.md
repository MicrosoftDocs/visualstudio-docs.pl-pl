---
title: Karta Ogólne, okno dialogowe właściwości procesu | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790504"
---
# <a name="general-tab-process-properties-dialog-box"></a>Karta ogólna, okno dialogowe właściwości procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
