---
title: Moduł wyliczający | Microsoft Docs
description: Elementy członkowskie tego modułu wyliczającego są używane dla funkcji TEXTOUTPROC, która jest funkcją wywołania zwrotnego udostępnianą przez ideę podczas wywołania funkcji SccOpenProject.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77c49f79ccdcfc4aa0325b89dfb38f3f8d4da721
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902595"
---
# <a name="message-enumerator"></a>Moduł wyliczający komunikat
Następujące flagi są używane dla funkcji , która jest funkcją wywołania zwrotnego udostępnianą przez ideę podczas wywołania `TEXTOUTPROC` [funkcji SccOpenProject](../extensibility/sccopenproject-function.md) (zobacz [LPTEXTOUTPROC,](../extensibility/lptextoutproc.md) aby uzyskać szczegółowe informacje na temat funkcji wywołania zwrotnego).

 Jeśli w idee zostanie poproszony o anulowanie procesu, może otrzymać jeden z komunikatów o anulowaniu. W takim przypadku wtyczka kontroli źródła używa opcji , aby poprosić `SCC_MSG_STARTCANCEL` ideę o wyświetlenie **przycisku Anuluj.** Następnie można wysłać dowolny zestaw normalnych komunikatów. Jeśli którykolwiek z tych zwraca `SCC_MSG_RTN_CANCEL` wartość , wtyczka zamyka operację i zwraca wartość . Wtyczka okresowo sonduje również w celu ustalenia, czy użytkownik `SCC_MSG_DOCANCEL` anulował operację. Gdy wszystkie operacje zostaną wykonane lub jeśli użytkownik je anuluje, wtyczka wyśle wiadomość `SCC_MSG_STOPCANCEL` . Typy , SCC_MSG_WARNING i SCC_MSG_ERROR są używane dla komunikatów, które są wyświetlane na `SCC_MSG_INFO` przewijanych listach komunikatów. `SCC_MSG_STATUS` to specjalny typ, który wskazuje, że tekst powinien być wyświetlany na pasku stanu lub w tymczasowym obszarze wyświetlania. Nie pozostaje trwale na liście.

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
 SCC_MSG_RTN_CANCEL z wywołania zwrotnego, aby wskazać anulowanie.

 SCC_MSG_RTN_OK wróć z wywołania zwrotnego, aby kontynuować.

 SCC_MSG_INFO Komunikat jest informacyjny.

 SCC_MSG_WARNING komunikat jest ostrzeżeniem.

 SCC_MSG_ERROR komunikat jest błędem.

 SCC_MSG_STATUS komunikat jest przeznaczony dla paska stanu.

 SCC_MSG_DOCANCEL Brak tekstu; Ide zwraca `SCC_MSG_RTN_OK` wartość lub `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL uruchamia pętlę anulowania.

 SCC_MSG_STOPCANCEL zatrzymuje pętlę anulowania.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
