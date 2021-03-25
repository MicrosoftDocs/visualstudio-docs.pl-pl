---
title: Procesy | Microsoft Docs
description: W tym artykule opisano definicje i rolę procesu w architekturze debugera w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 46e25ddfbe60e1b9ee456e586c6f424fc489f626
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067715"
---
# <a name="processes"></a>Procesy
W architekturze debugera, *proces*:

- Jest kontenerem dla zestawu programów. Jest to ściśle analogiczne do procesu systemu Windows, który jest kontenerem dla zestawu wątków.

- Może identyfikować siebie według nazwy, identyfikatora lub identyfikatora fizycznego.

- Może wyliczyć wszystkie uruchomione programy (i ich wątki).

- Może opisywać siebie, port, na którym działa program, oraz maszynę, która ją zawiera.

- Program może utworzyć jeden lub więcej programów, zakończyć każdy z tworzonych przez niego programów lub spowodować zatrzymanie programu.

- Jest reprezentowany przez interfejs [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , który jest tworzony podczas uruchamiania procesu. Proces jest uruchamiany przez Menedżera debugowania sesji (SDM) lub [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Pakiet debugowania może dołączyć aparat debugowania (Anuluj) do procesu przez wywołanie metody [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), co oznacza, że wszystkie możliwe programy działają w procesie, który może obsłużyć. Na przykład jeśli środowisko uruchomieniowe języka wspólnego nie dołącza do procesu, dołącza tylko do programów, które są uruchomione w kodzie zarządzanym.

## <a name="see-also"></a>Zobacz też
- [Programy](../../extensibility/debugger/programs.md)
- [Wątki](../../extensibility/debugger/threads.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Debuguj pakiet](../../extensibility/debugger/debug-package.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Dołącz](../../extensibility/debugger/reference/idebugprocess2-attach.md)
