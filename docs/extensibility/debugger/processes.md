---
title: Procesy | Microsoft Docs
description: W tym artykule opisano definicję i rolę procesu w architekturze debugera w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3cadf314b189c72320da3f54488af8560cf3fd8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901256"
---
# <a name="processes"></a>Procesy
W architekturze debugera *proces*:

- Jest kontenerem dla zestawu programów. Jest ona ściśle analogiczna do procesu systemu Windows, który jest kontenerem dla zestawu wątków.

- Może identyfikować się według nazwy, identyfikatora lub identyfikatora fizycznego.

- Może wyliczać wszystkie uruchomione programy (i ich wątki).

- Może opisywać samą siebie, port, na których działa, i maszynę, która go zawiera.

- Może tworzyć co najmniej jeden program, kończyć wszystkie programy, które tworzy, lub powodować zatrzymanie programu.

- Jest reprezentowany przez [interfejs IDebugProcess2,](../../extensibility/debugger/reference/idebugprocess2.md) który jest tworzony podczas uruchomiania procesu. Proces jest uruchamiany przez menedżera debugowania sesji (SDM) lub [LaunchSuspended.](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)

  Pakiet debugowania może dołączyć aparat debugowania (DE) do procesu przez wywołanie attach [,](../../extensibility/debugger/reference/idebugprocess2-attach.md)co oznacza, że DE dołącza do wszystkich możliwych programów uruchomionych w procesie, który może obsłużyć. Na przykład, jeśli środowisko uruchomieniowe języka wspólnego DE dołącza się do procesu, dołącza tylko do programów, które są uruchomione kodu zarządzanego.

## <a name="see-also"></a>Zobacz też
- [Programy](../../extensibility/debugger/programs.md)
- [Wątki](../../extensibility/debugger/threads.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Pakiet debugowania](../../extensibility/debugger/debug-package.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Dołącz](../../extensibility/debugger/reference/idebugprocess2-attach.md)
