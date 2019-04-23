---
title: Dołączanie do programu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c21b3e03eba03503c769e07ca2a2d90c24c59dc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045230"
---
# <a name="attach-to-the-program"></a>Dołącz do programu
Po zarejestrowaniu programy wpisz odpowiedni port, należy dołączyć debuger do programu, który chcesz debugować.

## <a name="choose-how-to-attach"></a>Wybierz sposób dołączania
 Istnieją trzy sposoby, w których Menedżer debugowania sesji (SDM) próbuje dołączyć do debugowanego programu.

1. Dla programów uruchamianych przez aparat debugowania za pośrednictwem [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) uzyskuje SDM — metoda (typowe interpretowanych języków, na przykład), [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfejs z [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) skojarzonego z programem dołączony do obiektu. Jeśli można uzyskać SDM `IDebugProgramNodeAttach2` następnie wywołuje interfejs SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody. `IDebugProgramNodeAttach2::OnAttach` Metoda zwraca `S_OK` oznacza, że nie dołączono go do programu i czy inne próby może również dołączyć do programu.

2. Jeśli model SDM można uzyskać [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) interfejsu programu dołączony do połączeń SDM [Dołącz](../../extensibility/debugger/reference/idebugprogramex2-attach.md) metody. To podejście jest typowy dla programów, które zostały uruchomione zdalnie przez dostawcę portu.

3. Jeśli program nie może zostać dołączony przez `IDebugProgramNodeAttach2::OnAttach` lub `IDebugProgramEx2::Attach` metody SDM ładuje aparat debugowania (Jeśli nie został jeszcze załadowany) przez wywołanie metody `CoCreateInstance` funkcji, a następnie wywołania [Dołącz](../../extensibility/debugger/reference/idebugengine2-attach.md) metody. To podejście jest typowy dla programów lokalnie uruchomić dostawcy portu.

    Istnieje również możliwość dla dostawcy port niestandardowy wywołać `IDebugEngine2::Attach` metody w implementacji dostawcy portu niestandardowego `IDebugProgramEx2::Attach` metody. Zwykle w tym przypadku portu niestandardowego dostawcy spowoduje uruchomienie aparatu debugowania na komputerze zdalnym.

   Załącznik jest osiągana, gdy Menedżer debugowania sesji (SDM) wywołuje [Dołącz](../../extensibility/debugger/reference/idebugengine2-attach.md) metody.

   Jeśli uruchomienie usługi DE w tym samym procesie co aplikacja do debugowania, a następnie należy zaimplementować następujące metody [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Po `IDebugEngine2::Attach` metoda jest wywoływana, wykonaj następujące kroki w danej implementacji `IDebugEngine2::Attach` metody:

1. Wyślij [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) obiekt zdarzenia do SDM. Aby uzyskać więcej informacji, zobacz [wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).

2. Wywołaj [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metody [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) obiektu, który został przekazany do `IDebugEngine2::Attach` metody.

     Spowoduje to zwrócenie `GUID` używany do identyfikacji programu. `GUID` Muszą być przechowywane w obiekcie, że reprezentuje lokalnej do DE i programu musi zwracane, gdy `IDebugProgram2::GetProgramId` wywoływana jest metoda `IDebugProgram2` interfejsu.

    > [!NOTE]
    >  W przypadku zaimplementowania `IDebugProgramNodeAttach2` interfejsu programu `GUID` jest przekazywany do `IDebugProgramNodeAttach2::OnAttach` metody. To `GUID` jest wykorzystywany przez program `GUID` zwrócone przez `IDebugProgram2::GetProgramId` metody.

3. Wyślij [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzeń obiektowi powiadomić SDM, lokalnej `IDebugProgram2` do reprezentowania program DE został utworzony obiekt. Aby uzyskać więcej informacji, zobacz [wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    >  To nie jest taka sama `IDebugProgram2` obiektu, który został przekazany do `IDebugEngine2::Attach` metody. Wcześniej przekazane `IDebugProgram2` obiekt jest rozpoznawany przez tylko portu i jest oddzielnym obiektem.

## <a name="see-also"></a>Zobacz także
- [Dołączanie na podstawie uruchamiania](../../extensibility/debugger/launch-based-attachment.md)
- [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
