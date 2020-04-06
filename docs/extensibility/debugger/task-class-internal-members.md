---
title: Klasa zadania — członkowie wewnętrzni | Dokumenty firmy Microsoft
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
ms.openlocfilehash: dcf278c0248b344cea4be7cf161ecc91581f5f2e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712732"
---
# <a name="task-class---internal-members"></a>Klasa zadań — elementy wewnętrzne
W tym artykule opisano <xref:System.Threading.Tasks.Task?displayProperty=fullName> wewnętrznych członków klasy, które pomagają zaimplementować debugera niestandardowego. Aby uzyskać ogólne informacje na <xref:System.Threading.Tasks.Task> temat tej klasy, zobacz artykuł referencyjny.

 **Obszar nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaż:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z programu .NET Framework, następująca składnia znajduje się we wspólnym języku pośrednim (CIL).

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
|[Metoda NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Metoda zastępcza używana jako miejsce docelowe punktu przerwania przez debuger.|

### <a name="fields"></a>Pola

|Nazwa|Opis|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Pełnomocnik, który reprezentuje kod do <xref:System.Threading.Tasks.Task> wykonania w obiekcie.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Przechowuje dodatkowe właściwości <xref:System.Threading.Tasks.Task> obiektu.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Pole zapasowe <xref:System.Threading.Tasks.Task?displayProperty=fullName> właściwości nadrzędnej.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Przechowuje informacje o bieżącym <xref:System.Threading.Tasks.Task> stanie obiektu.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Obiekt, który reprezentuje dane, które będą używane przez akcję.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Pole podkładu <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> dla właściwości.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Następny dostępny identyfikator <xref:System.Threading.Tasks.Task> obiektu.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Wskazuje, że zadanie zostało anulowane przed osiągnięciem stanu uruchomionego lub że zadanie potwierdziło jego anulowanie i zostało ukończone bez wyjątku.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Wskazuje, że zadanie jest uruchomione.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Wskazuje, że zadanie zostało ukończone z powodu nieobsługiwał wyjątek.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Wskazuje, że zadanie zostało pomyślnie wykonane.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Wskazuje, że zadanie zakończone wykonywanie jego delegata i niejawnie czeka na dołączone zadania podrzędne, aby zakończyć.|

## <a name="remarks"></a>Uwagi
 Następujące metody wewnętrzne są przydatne dla aparatu debugera, ponieważ oznaczają one wejście do <xref:System.Threading.Tasks.Task> wykonania kodu:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Zobacz też
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Wewnętrzne rozszerzenia równoległego dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
