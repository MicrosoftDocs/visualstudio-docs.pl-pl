---
title: Dołączanie do programu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f39b489a57ab93ba5f2d116738c591bd53ff95f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739242"
---
# <a name="attach-to-the-program"></a>Dołącz do programu
Po zarejestrowaniu programów przy odpowiednim porcie należy dołączyć debuger do programu, który ma zostać debugowany.

## <a name="choose-how-to-attach"></a>Wybieranie sposobu dołączania
 Istnieją trzy sposoby, w którym menedżer debugowania sesji (SDM) próbuje dołączyć do debugowanego programu.

1. W przypadku programów uruchamianych przez aparat debugowania za pomocą metody [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (typowej dla języków interpretowanych, na przykład), moduł SDM uzyskuje interfejs [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) z obiektu [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) skojarzonego z dołączonym programem. Jeśli SDM można `IDebugProgramNodeAttach2` uzyskać interfejs, SDM następnie wywołuje [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody. Metoda `IDebugProgramNodeAttach2::OnAttach` zwraca, `S_OK` aby wskazać, że nie dołączyć do programu i że można podjąć inne próby dołączenia do programu.

2. Jeśli SDM można uzyskać interfejs [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) z programu podłączonego do, SDM wywołuje [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) metody. Takie podejście jest typowe dla programów, które zostały uruchomione zdalnie przez dostawcę portu.

3. Jeśli program nie może być `IDebugProgramNodeAttach2::OnAttach` `IDebugProgramEx2::Attach` dołączony za pośrednictwem lub metody, SDM ładuje aparat debugowania (jeśli nie jest już załadowany) przez wywołanie `CoCreateInstance` funkcji, a następnie wywołuje [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metody. Takie podejście jest typowe dla programów uruchamianych lokalnie przez dostawcę portu.

    Jest również możliwe dla dostawcy portu `IDebugEngine2::Attach` niestandardowego wywołać metodę w niestandardowej dostawcy portu implementacji `IDebugProgramEx2::Attach` metody. Zazwyczaj w tym przypadku dostawca portu niestandardowego uruchamia aparat debugowania na komputerze zdalnym.

   Załącznik jest osiągany, gdy menedżer debugowania sesji (SDM) wywołuje [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metody.

   Jeśli uruchomisz de w tym samym procesie co aplikacja, która ma być debugowana, należy zaimplementować następujące metody [IDebugProgramNode2:](../../extensibility/debugger/reference/idebugprogramnode2.md)

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Po `IDebugEngine2::Attach` wywołaniu metody wykonaj następujące kroki w `IDebugEngine2::Attach` implementacji metody:

1. Wyślij obiekt zdarzenia [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM. Aby uzyskać więcej informacji, zobacz [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).

2. Wywołanie [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metody na [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) obiektu, `IDebugEngine2::Attach` który został przekazany do metody.

     Zwraca to, `GUID` który jest używany do identyfikowania programu. Musi `GUID` być przechowywany w obiekcie, który reprezentuje program lokalny do DE `IDebugProgram2::GetProgramId` i musi `IDebugProgram2` zostać zwrócony, gdy metoda jest wywoływana w interfejsie.

    > [!NOTE]
    > Jeśli zaimplementujesz `IDebugProgramNodeAttach2` interfejs, `GUID` program jest `IDebugProgramNodeAttach2::OnAttach` przekazywany do metody. Jest `GUID` to używane dla `GUID` programu zwracane przez `IDebugProgram2::GetProgramId` metodę.

3. Wyślij obiekt zdarzenia [IDebugProgramCreateEvent2,](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) aby powiadomić `IDebugProgram2` SDM, że obiekt lokalny został utworzony w celu reprezentowania programu do DE. Aby uzyskać szczegółowe informacje, zobacz [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Nie jest to `IDebugProgram2` ten sam obiekt, który został przekazany do `IDebugEngine2::Attach` metody. Poprzednio przekazany `IDebugProgram2` obiekt jest rozpoznawany tylko przez port i jest oddzielnym obiektem.

## <a name="see-also"></a>Zobacz też
- [Załącznik oparty na uruchamianiu](../../extensibility/debugger/launch-based-attachment.md)
- [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Dołącz](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Dołącz](../../extensibility/debugger/reference/idebugengine2-attach.md)
