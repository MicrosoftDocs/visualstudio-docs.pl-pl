---
title: Wyliczacz wiadomości | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702505"
---
# <a name="message-enumerator"></a>Wyliczacz wiadomości
Następujące flagi są używane `TEXTOUTPROC` dla funkcji, która jest funkcją wywołania zwrotnego, który IDE zapewnia, gdy wywołuje [SccOpenProject](../extensibility/sccopenproject-function.md) (zobacz [LPTEXTOUTPROC,](../extensibility/lptextoutproc.md) aby uzyskać szczegółowe informacje na temat funkcji wywołania zwrotnego).

 Jeśli IDE zostanie poproszony o anulowanie procesu, może uzyskać jedną z wiadomości anuluj. W takim przypadku wtyczka kontroli źródła `SCC_MSG_STARTCANCEL` używa do zwrócenia się do IDE, aby wyświetlić przycisk **Anuluj.** Następnie może zostać wysłany dowolny zestaw normalnych wiadomości. Jeśli którykolwiek `SCC_MSG_RTN_CANCEL`z tych zwraca , wtyczka kończy operację i zwraca. Wtyczka również sonduje `SCC_MSG_DOCANCEL` okresowo, aby ustalić, czy użytkownik anulował operację. Po zakończeniu wszystkich operacji lub anulowaniu przez użytkownika wtyczka `SCC_MSG_STOPCANCEL`wysyła . Typy `SCC_MSG_INFO`SCC_MSG_WARNING i SCC_MSG_ERROR są używane dla wiadomości, które są wyświetlane na przewijanej liście wiadomości. `SCC_MSG_STATUS`to specjalny typ, który wskazuje, że tekst powinien być wyświetlany na pasku stanu lub w tymczasowym obszarze wyświetlania. Nie pozostaje na stałe na liście.

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
 SCC_MSG_RTN_CANCEL Powrót z wywołania zwrotnego, aby wskazać anuluj.

 SCC_MSG_RTN_OK Powrót z wywołania zwrotnego, aby kontynuować.

 SCC_MSG_INFO Wiadomość ma informacyjny.

 SCC_MSG_WARNING Komunikat jest ostrzeżeniem.

 SCC_MSG_ERROR Komunikat jest błędem.

 SCC_MSG_STATUS Message jest przeznaczony dla paska stanu.

 SCC_MSG_DOCANCEL Brak tekstu; IDE `SCC_MSG_RTN_OK` zwraca `SCC_MSG_RTN_CANCEL`lub .

 SCC_MSG_STARTCANCEL Uruchamia pętlę anulowania.

 SCC_MSG_STOPCANCEL Zatrzymuje pętlę anulowania.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
