---
title: Moduł wyliczający komunikat | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37932ce6e64361692d659355e9ab6e88ee5462ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806501"
---
# <a name="message-enumerator"></a>Moduł wyliczający komunikat
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
 SCC_MSG_RTN_CANCEL zwracanie z wywołania zwrotnego w celu wskazania, Anuluj.

 SCC_MSG_RTN_OK powrót z wywołania zwrotnego, aby kontynuować.

 Komunikat SCC_MSG_INFO ma charakter informacyjny.

 Komunikat SCC_MSG_WARNING jest ostrzeżenie.

 Komunikat SCC_MSG_ERROR, występuje błąd.

 SCC_MSG_STATUS wiadomość jest przeznaczona dla paska stanu.

 Tekst nie SCC_MSG_DOCANCEL; Zwraca IDE `SCC_MSG_RTN_OK` lub `SCC_MSG_RTN_CANCEL`.

 SCC_MSG_STARTCANCEL rozpoczyna się na anulowanie pętli.

 SCC_MSG_STOPCANCEL zatrzymuje pętli anulowania.

## <a name="see-also"></a>Zobacz także
- [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)