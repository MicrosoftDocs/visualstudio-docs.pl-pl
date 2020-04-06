---
title: Powiadamianie portu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738326"
---
# <a name="notify-the-port"></a>Powiadamianie portu
Po uruchomieniu programu, port musi być powiadomiony, w następujący sposób:

1. Gdy port odbiera nowy węzeł programu, wysyła zdarzenie tworzenia programu z powrotem do sesji debugowania. Zdarzenie niesie ze sobą interfejs, który reprezentuje program.

2. Sesja debugowania wysyła zapytanie do programu o identyfikator aparatu debugowania (DE), do których można dołączyć.

3. Sesja debugowania sprawdza, czy DE znajduje się na liście dopuszczalnych DEs dla tego programu. Sesja debugowania pobiera tę listę z aktywnych ustawień programu rozwiązania, pierwotnie przekazanych do niej przez pakiet debugowania.

    DE musi znajdować się na liście dopuszczalnych, w przeciwnym razie DE nie zostanie dołączony do programu.

   Programowo, gdy port po raz pierwszy odbiera nowy węzeł programu, tworzy interfejs [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) do reprezentowania programu.

> [!NOTE]
> Nie należy mylić `IDebugProgram2` tego z interfejsem utworzonym później przez aparat debugowania (DE).

 Port wysyła zdarzenie tworzenia programu [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) z powrotem do menedżera debugowania `IConnectionPoint` sesji (SDM) za pomocą interfejsu COM.

> [!NOTE]
> Nie należy tego mylić z interfejsem, `IDebugProgramCreateEvent2` który jest wysyłany później przez DE.

 Wraz z samym interfejsem zdarzenia port wysyła interfejsy [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)i [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) które reprezentują odpowiednio port, proces i program. SDM wywołuje [IDebugProgram2::GetEngineInfo,](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) aby uzyskać identyfikator GUID DE, który może debugować program. Identyfikator GUID został pierwotnie uzyskany z interfejsu [IDebugProgramNode2.](../../extensibility/debugger/reference/idebugprogramnode2.md)

 SDM sprawdza, czy DE znajduje się na liście dopuszczalnych DE. SDM pobiera tę listę z aktywnych ustawień programu rozwiązania, pierwotnie przekazywane do niego przez pakiet debugowania. De musi znajdować się na liście dopuszczalnych, w przeciwnym razie nie będzie dołączony do programu.

 Gdy tożsamość DE jest znana, SDM jest gotowy do dołączenia go do programu.

## <a name="see-also"></a>Zobacz też
- [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)
- [Dołączanie po uruchomieniu](../../extensibility/debugger/attaching-after-a-launch.md)
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
