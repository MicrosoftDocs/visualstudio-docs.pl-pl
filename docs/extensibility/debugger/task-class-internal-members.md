---
title: Task, klasa — składowe | Microsoft Docs
description: Dowiedz się więcej o wewnętrznych składowych klasy System.Threading.Tasks.Task, które ułatwiają implementowanie debugera niestandardowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 37691714d0168594b61a1a3849f7b65264e9999e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902894"
---
# <a name="task-class---internal-members"></a>Task, klasa — składowe wewnętrzne
W tym artykule opisano wewnętrzne składowe klasy, które ułatwiają <xref:System.Threading.Tasks.Task?displayProperty=fullName> implementowanie debugera niestandardowego. Aby uzyskać ogólne informacje o tej klasie, zobacz <xref:System.Threading.Tasks.Task> artykuł referencyjny.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z .NET Framework, w języku CIL (Common Intermediate Language) znajduje się następująca składnia.

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
|[Metoda SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Ustawia lub czyszczy bit TASK_STATE_WAIT_COMPLETION_NOTIFICATION stanu.|
|[Metoda NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Metoda symbolu zastępczego używana jako element docelowy punktu przerwania przez debuger.|

### <a name="fields"></a>Pola

|Nazwa|Opis|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Delegat reprezentujący kod do wykonania w <xref:System.Threading.Tasks.Task> obiekcie .|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Przechowuje dodatkowe właściwości <xref:System.Threading.Tasks.Task> obiektu.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Pole zapasowe właściwości <xref:System.Threading.Tasks.Task?displayProperty=fullName> nadrzędnej.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Przechowuje informacje o bieżącym stanie <xref:System.Threading.Tasks.Task> obiektu.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Obiekt reprezentujący dane, które będą używane przez akcję.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Pole zapasowe właściwości <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> .|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Następny dostępny identyfikator <xref:System.Threading.Tasks.Task> obiektu.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Wskazuje, że zadanie zostało anulowane przed osiągnięciem stanu uruchomienia lub że zadanie potwierdza jego anulowanie i zostało ukończone bez wyjątku.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Wskazuje, że zadanie jest uruchomione.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Wskazuje, że zadanie zostało ukończone z powodu nieobsługiwanego wyjątku.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Wskazuje, że zadanie zakończyło się pomyślnie.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Wskazuje, że zadanie zakończyło wykonywanie delegata i niejawnie oczekuje na zakończenie dołączonych zadań podrzędnych.|

## <a name="remarks"></a>Uwagi
 Następujące metody wewnętrzne są przydatne dla aparatu debugera, ponieważ oznaczają one wejście do <xref:System.Threading.Tasks.Task> wykonywania kodu:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Zobacz też
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Równoległe wewnętrzne rozszerzenia dla .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
