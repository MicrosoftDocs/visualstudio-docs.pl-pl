---
title: Moduł wyliczający komunikat | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194341"
---
# <a name="message-enumerator"></a>Moduł wyliczający komunikat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następujące flagi są używane do `TEXTOUTPROC` funkcji, która jest funkcją wywołania zwrotnego, która zapewnia środowisko IDE, gdy wywołuje [SccOpenProject](../extensibility/sccopenproject-function.md) (zobacz [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) szczegółowe informacje na temat wywołania zwrotnego Funkcja).  
  
 Jeśli środowisko IDE jest pytanie, aby anulować proces, jego może zostać komunikatów Anuluj. W tym przypadku źródło sterowania wtyczka używa `SCC_MSG_STARTCANCEL` poprosić IDE, aby wyświetlić **anulować** przycisku. Po tym dowolny zbiór normalne komunikaty mogą być wysyłane. Jeśli dowolny z tych zwraca `SCC_MSG_RTN_CANCEL`, a następnie kończy działanie operacji i zwraca dodatku typu plug-in. Wtyczka również sonduje `SCC_MSG_DOCANCEL` okresowo, aby określić, jeśli użytkownik anulował operację. Gdy wszystkie operacje są wykonywane lub jeśli użytkownik anulował, wysyła wtyczki `SCC_MSG_STOPCANCEL`. `SCC_MSG_INFO`, SCC_MSG_WARNING, oraz typy SCC_MSG_ERROR są używane do wiadomości, które Pobierz wyświetlane na liście przewijania wiadomości. `SCC_MSG_STATUS` to specjalny typ, który wskazuje, że tekst powinny być widoczne w pasku stanu lub obszaru tymczasowego wyświetlania. Nie ona trwale na liście.  
  
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
 Powrót z wywołania zwrotnego, aby wskazać, Anuluj.  
  
 SCC_MSG_RTN_OK  
 Powrót z wywołania zwrotnego, aby kontynuować.  
  
 SCC_MSG_INFO  
 Komunikat ma charakter informacyjny.  
  
 SCC_MSG_WARNING  
 Komunikat jest ostrzeżenie.  
  
 SCC_MSG_ERROR  
 Komunikat błędu.  
  
 SCC_MSG_STATUS  
 Wiadomość jest przeznaczona dla paska stanu.  
  
 SCC_MSG_DOCANCEL  
 Brak tekstu; Zwraca IDE `SCC_MSG_RTN_OK` lub `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Uruchamia pętli anulowania.  
  
 SCC_MSG_STOPCANCEL  
 Zatrzymuje pętli anulowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
