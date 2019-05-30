---
title: Procesy | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c45fc70fe61c7221a8042d275dd44d69eb5d11e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351499"
---
# <a name="processes"></a>Procesy
W architekturze debugera *procesu*:

- To kontener dla zestawu programów. Jest ściśle analogiczne do procesu Windows, który jest kontenerem dla zestawu wątków.

- Można zidentyfikować sama nazwa, identyfikator lub identyfikator fizycznych.

- Można wyliczyć wszystkie uruchomione programy (i ich wątków).

- Można opisać, port, na którym jest uruchomiona w i komputer który go zawiera.

- Można utworzyć jeden lub więcej programów zakończenie dowolnych programów, które tworzy i spowodować, że program przestanie.

- Jest reprezentowany przez [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interfejs, który jest tworzony, gdy proces jest uruchamiany. Proces jest uruchamiany przez albo Menedżer debugowania sesji (SDM) lub [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Pakiet debugowania można dołączyć aparat debugowania (DE) do procesu przez wywołanie metody [Dołącz](../../extensibility/debugger/reference/idebugprocess2-attach.md), co oznacza, że Niemcy dołącza wszystkie możliwe programy działający w procesie, który może obsługiwać. Na przykład jeśli środowisko uruchomieniowe języka wspólnego DE dołącza do procesu, dołącza tylko do programów uruchomionych w kodzie zarządzanym.

## <a name="see-also"></a>Zobacz także
- [Programy](../../extensibility/debugger/programs.md)
- [Wątki](../../extensibility/debugger/threads.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Pakiet debugowania](../../extensibility/debugger/debug-package.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)