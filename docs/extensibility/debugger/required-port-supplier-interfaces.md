---
title: Wymagane interfejsy dostawcy portów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2aeb1f26f81d773e171aa3fed6b0f2ef976c91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713149"
---
# <a name="required-port-supplier-interfaces"></a>Wymagane interfejsy dostawcy portów
Dostawca portu musi implementować interfejs [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) . [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Dostawca portu dostarcza porty i implementuje je. W związku z tym musi uruchamiać następujące interfejsy:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Opisuje port i wylicza wszystkie procesy działające na porcie.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Zapewnia uruchamianie i kończenie procesów na porcie.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Zapewnia mechanizm dla programów uruchomionych w kontekście tego portu w celu powiadomienia go o tworzeniu i zniszczeniu węzła programu. Aby uzyskać więcej informacji, zobacz [węzły programów](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Udostępnia punkt połączenia dla [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).

## <a name="port-supplier-operation"></a>Operacja dostawcy portu
 Ujścia [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) odbiera powiadomienia, gdy proces i programy są tworzone i niszczone na porcie. Port jest wymagany do wysyłania [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) podczas tworzenia procesu i [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) , gdy proces zostanie zniszczony na porcie. Port jest również wymagany do wysyłania [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) podczas tworzenia programu i [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) , gdy program zostanie zniszczony w procesie uruchomionym na porcie.

 Port zazwyczaj wysyła i niszczy zdarzenia w odpowiedzi odpowiednio do metod [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) i [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) .

 Ponieważ port może uruchamiać i kończyć zarówno procesy fizyczne, jak i programy logiczne, następujące interfejsy muszą być również zaimplementowane przez aparat debugowania:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Opisuje proces fizyczny. Należy zaimplementować co najmniej następujące metody:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Zapewnia sposób dołączania i odłączania modelu SDM do procesu.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Zawiera opis programu logicznego. Należy zaimplementować co najmniej następujące metody:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess —](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Umożliwia dołączenie modelu SDM do tego programu.

## <a name="see-also"></a>Zobacz też
- [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)
