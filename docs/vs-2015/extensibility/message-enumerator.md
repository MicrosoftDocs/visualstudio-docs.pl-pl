---
title: Moduł wyliczający komunikatów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bd42c825cd45068e13178856e524268b426ec53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194341"
---
# <a name="message-enumerator"></a>Moduł wyliczający komunikat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniższe flagi są używane dla `TEXTOUTPROC` funkcji, która jest funkcją wywołania zwrotnego, która zapewnia IDE, gdy wywołuje [SccOpenProject](../extensibility/sccopenproject-function.md) (zobacz [lpTextOutProc](../extensibility/lptextoutproc.md) , aby uzyskać szczegółowe informacje o funkcji wywołania zwrotnego).  
  
 Jeśli w środowisku IDE zostanie wyświetlony monit o anulowanie procesu, może zostać wyświetlony jeden z komunikatów anulowania. W takim przypadku wtyczka do kontroli źródła używa `SCC_MSG_STARTCANCEL` do poproszenia IDE o wyświetlenie przycisku **Anuluj** . Po wykonaniu tej opcji można wysłać dowolny zestaw zwykłych komunikatów. Jeśli którykolwiek z tych zwraca `SCC_MSG_RTN_CANCEL` , wtyczka kończy operację i zwraca wartość. Wtyczka również sonduje `SCC_MSG_DOCANCEL` okresowo, aby określić, czy użytkownik anulował operację. Po zakończeniu wszystkich operacji lub anulowaniu wtyczki przez użytkownika `SCC_MSG_STOPCANCEL` . `SCC_MSG_INFO`Typy, SCC_MSG_WARNING i SCC_MSG_ERROR są używane w przypadku komunikatów, które są wyświetlane na przewijanej liście komunikatów. `SCC_MSG_STATUS` jest typem specjalnym, który wskazuje, że tekst powinien być wyświetlany na pasku stanu lub w tymczasowym obszarze wyświetlania. Nie pozostaje na stałe na liście.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 SCC_MSG_RTN_CANCEL  
 Wróć z wywołania zwrotnego, aby wskazać przycisk Anuluj.  
  
 SCC_MSG_RTN_OK  
 Wróć z wywołania zwrotnego, aby kontynuować.  
  
 SCC_MSG_INFO  
 Komunikat ma informacje.  
  
 SCC_MSG_WARNING  
 Komunikat jest ostrzeżeniem.  
  
 SCC_MSG_ERROR  
 Komunikat jest błędem.  
  
 SCC_MSG_STATUS  
 Komunikat jest przeznaczony dla paska stanu.  
  
 SCC_MSG_DOCANCEL  
 Brak tekstu; IDE zwraca `SCC_MSG_RTN_OK` lub `SCC_MSG_RTN_CANCEL` .  
  
 SCC_MSG_STARTCANCEL  
 Uruchamia pętlę anulowania.  
  
 SCC_MSG_STOPCANCEL  
 Kończy pętlę anulowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
