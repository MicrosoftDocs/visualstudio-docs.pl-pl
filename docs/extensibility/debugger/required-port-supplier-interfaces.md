---
title: Wymagane interfejsy dostawców portów | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713149"
---
# <a name="required-port-supplier-interfaces"></a>Wymagane interfejsy dostawców portów
Dostawca portu musi implementować interfejs [IDebugPortSupplier2.](../../extensibility/debugger/reference/idebugportsupplier2.md) [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Dostawca portu dostarcza porty i wdraża je. W związku z tym należy uruchomić następujące interfejsy:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Opisuje port i wylicza wszystkie procesy uruchomione na porcie.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Zapewnia uruchamianie i zamykanie procesów na porcie.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Udostępnia mechanizm dla programów uruchomionych w kontekście tego portu, aby powiadomić go o tworzeniu i niszczeniu węzła programu. Aby uzyskać więcej informacji, zobacz [Węzły programu](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Udostępnia punkt połączenia dla [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).

## <a name="port-supplier-operation"></a>Obsługa dostawcy portu
 Umywalka [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) odbiera powiadomienia, gdy proces i programy są tworzone i niszczone na porcie. Port jest wymagany do [wysyłania IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) podczas tworzenia procesu i [IDebugProcessDestroyEvent2,](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) gdy proces zostanie zniszczony na porcie. Port jest również wymagany do [wysyłania IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) podczas tworzenia programu i [IDebugProgramDestroyEvent2,](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) gdy program zostanie zniszczony w procesie uruchomionym na porcie.

 Port zazwyczaj wysyła program tworzenia i niszczenia zdarzeń w odpowiedzi na [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) i [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) metody, odpowiednio.

 Ponieważ port może uruchamiać i kończyć zarówno procesy fizyczne, jak i programy logiczne, aparat debugowania musi również zaimplementować następujące interfejsy:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Opisuje proces fizyczny. Należy wdrożyć co najmniej następujące metody:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId (ida getprocessid)](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Umożliwia sdm dołączyć i odłączyć się od procesu.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Opisuje program logiczny. Należy wdrożyć co najmniej następujące metody:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess ( GetProcess )](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Umożliwia dołączenie sdm do tego programu.

## <a name="see-also"></a>Zobacz też
- [Wdrażanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)
