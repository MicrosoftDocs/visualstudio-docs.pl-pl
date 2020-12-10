---
title: Task — Klasa — składowe wewnętrzne | Microsoft Docs
description: Zapoznaj się z wewnętrznymi elementami członkowskimi klasy System. Threading. Tasks. Task, która ułatwia implementowanie niestandardowego debugera.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f18de66a524fbc652b8153c5b34b4464cda60f5
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996022"
---
# <a name="task-class---internal-members"></a>Task — Klasa — składowe wewnętrzne
W tym artykule opisano wewnętrzne elementy członkowskie <xref:System.Threading.Tasks.Task?displayProperty=fullName> klasy, które ułatwiają zaimplementowanie niestandardowego debugera. Aby uzyskać ogólne informacje o tej klasie, zobacz <xref:System.Threading.Tasks.Task> artykuł referencyjny.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z .NET Framework, następująca składnia jest udostępniana w typowym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.class public auto ansi System.Threading.Tasks.Task
       extends System.Object
       implements System.Threading.IThreadPoolWorkItem,
                  System.IAsyncResult,
                  System.IDisposable,
                  System.Threading.ICancelableOperation
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[Metoda SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Ustawia lub czyści bit stanu TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|
|[Metoda NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Metoda zastępcza używana jako docelowy punkt przerwania przez debuger.|

### <a name="fields"></a>Pola

|Nazwa|Opis|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Delegat reprezentujący kod do wykonania w <xref:System.Threading.Tasks.Task> obiekcie.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Przechowuje dodatkowe właściwości <xref:System.Threading.Tasks.Task> obiektu.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Pole zapasowe dla <xref:System.Threading.Tasks.Task?displayProperty=fullName> Właściwości nadrzędnej.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Przechowuje informacje o bieżącym stanie <xref:System.Threading.Tasks.Task> obiektu.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Obiekt reprezentujący dane, które będą używane przez akcję.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Pole zapasowe <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> właściwości.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Następny dostępny identyfikator <xref:System.Threading.Tasks.Task> obiektu.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Wskazuje, że zadanie zostało anulowane przed osiągnięciem stanu uruchomienia lub że zadanie potwierdziło jego anulowanie i ukończone bez wyjątku.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Wskazuje, że zadanie jest uruchomione.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Wskazuje, że zadanie zostało ukończone z powodu nieobsługiwanego wyjątku.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Wskazuje, że zadanie zostało ukończone pomyślnie.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Wskazuje, że zadanie zakończyło wykonywanie delegata i nieoczekiwanie oczekuje na zakończenie dołączonych zadań podrzędnych.|

## <a name="remarks"></a>Uwagi
 Następujące metody wewnętrzne są przydatne dla aparatu debugera, ponieważ oznaczają wejście do <xref:System.Threading.Tasks.Task> wykonania kodu:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Zobacz też
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Wewnętrzne rozszerzenia równoległe dla .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
