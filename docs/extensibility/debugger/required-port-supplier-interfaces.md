---
title: Wymagane interfejsy dostawcy portów | Microsoft Docs
description: Dowiedz się więcej o interfejsach, które musi uruchomić dostawca portu. Dostawca portów dostarcza porty i je implementuje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96cf70302839a9de3c5fb0fec01136d9700ee17e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902374"
---
# <a name="required-port-supplier-interfaces"></a>Wymagane interfejsy dostawcy portów
Dostawca portu musi zaimplementować [interfejs IDebugPortSupplier2.](../../extensibility/debugger/reference/idebugportsupplier2.md) [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Dostawca portów dostarcza porty i je implementuje. W związku z tym musi działać następujące interfejsy:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Opisuje port i wylicza wszystkie procesy uruchomione na porcie.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Umożliwia uruchamianie i końowanie procesów na porcie.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Udostępnia mechanizm dla programów uruchomionych w kontekście tego portu w celu powiadamiania o tworzeniu i likwidacji węzłów programu. Aby uzyskać więcej informacji, zobacz [Węzły programu](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Udostępnia punkt połączenia dla [IDebugPortEvents2.](../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="port-supplier-operation"></a>Operacja dostawcy portów
 [Ujścia IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) odbiera powiadomienia, gdy proces i programy są tworzone i niszczone na porcie. Port jest wymagany do wysyłania [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) podczas tworzenia procesu i [IDebugProcessDestroyEvent2,](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) gdy proces jest niszczony na porcie. Port jest również wymagany do wysyłania [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) podczas tworzenia programu i [IDebugProgramDestroyEvent2,](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) gdy program jest niszczony w procesie uruchomionym na porcie.

 Port zazwyczaj wysyła zdarzenia tworzenia i niszczenia programu w odpowiedzi odpowiednio na metody [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) i [RemoveProgramNode.](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)

 Ponieważ port może uruchamiać i kończyć zarówno procesy fizyczne, jak i programy logiczne, aparat debugowania musi również zaimplementować następujące interfejsy:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Opisuje proces fizyczny. Należy zaimplementować co najmniej następujące metody:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Umożliwia programowi SDM dołączanie się do procesu i odłączanie go od procesu.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Opisuje program logiczny. Należy zaimplementować co najmniej następujące metody:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Umożliwia programowi SDM dołączenie do tego programu.

## <a name="see-also"></a>Zobacz też
- [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)
