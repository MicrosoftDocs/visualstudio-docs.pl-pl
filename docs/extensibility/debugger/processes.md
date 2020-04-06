---
title: Procesy | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c59b90bb117dded0f528bc33a617370b091a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738248"
---
# <a name="processes"></a>Procesy
W architekturze debugera *proces:*

- Jest kontenerem dla zestawu programów. Jest to ściśle analogiczne do procesu systemu Windows, który jest kontenerem dla zestawu wątków.

- Może identyfikować się za pomocą nazwy, identyfikatora lub identyfikatora fizycznego.

- Można wyliczyć wszystkie uruchomione programy (i ich wątki).

- Można opisać siebie, port, w którym działa i komputer, który go zawiera.

- Można utworzyć jeden lub więcej programów, zakończyć dowolny z programów, które tworzy, lub spowodować zatrzymanie programu.

- Jest reprezentowany przez interfejs [IDebugProcess2,](../../extensibility/debugger/reference/idebugprocess2.md) który jest tworzony po uruchomieniu procesu. Proces jest uruchamiany przez menedżera debugowania sesji (SDM) lub [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Pakiet debugowania można dołączyć aparat debugowania (DE) do procesu, wywołując [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), co oznacza, że DE dołącza do wszystkich możliwych programów uruchomionych w procesie, który może obsłużyć. Na przykład jeśli środowisko wykonawcze języka wspólnego DE dołącza do procesu, dołącza tylko do programów, które są uruchomione kod zarządzany.

## <a name="see-also"></a>Zobacz też
- [Programy](../../extensibility/debugger/programs.md)
- [Wątki](../../extensibility/debugger/threads.md)
- [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md)
- [Pakiet debugowania](../../extensibility/debugger/debug-package.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Dołącz](../../extensibility/debugger/reference/idebugprocess2-attach.md)
