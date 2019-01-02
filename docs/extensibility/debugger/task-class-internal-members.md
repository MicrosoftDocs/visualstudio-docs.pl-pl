---
title: Task, klasa — składowe wewnętrzne | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 34c8da8d661dcb0a8096576617403209a0a70c56
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872794"
---
# <a name="task-class---internal-members"></a>Task — klasa — składowe wewnętrzne
W tym artykule opisano wewnętrznych członków <xref:System.Threading.Tasks.Task?displayProperty=fullName> klasy, które pomagają implementacji niestandardowego debugera. Aby uzyskać ogólne informacje dotyczące tej klasy, zobacz <xref:System.Threading.Tasks.Task> artykule dotyczącym struktury.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w *mscorlib.dll*)  
  
 Ponieważ nie można uzyskać dostępu do tych wewnętrznych składowych z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
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
|[Metoda SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Ustawia lub czyści stan TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|  
|[Metoda NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Metoda symbolu zastępczego używany jako obiekt docelowy punkt przerwania przez debuger.|  
  
### <a name="fields"></a>Pola  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|Delegat, który reprezentuje kod do wykonania w <xref:System.Threading.Tasks.Task> obiektu.|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Przechowuje dodatkowe właściwości <xref:System.Threading.Tasks.Task> obiektu.|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Pole zapasowe dla <xref:System.Threading.Tasks.Task?displayProperty=fullName> nadrzędnej właściwość.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Przechowuje informacje o bieżącym stanie <xref:System.Threading.Tasks.Task> obiektu.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Obiekt, który reprezentuje dane, które będą używane przez akcję.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Pole zapasowe dla <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> właściwości.|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Następny dostępny identyfikator <xref:System.Threading.Tasks.Task> obiektu.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Wskazuje, że zadanie zostało anulowane przed osiągnięciem stanu uruchomienia lub potwierdza jej anulowania i ukończone bez wyjątku zadania.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Wskazuje, że zadanie jest uruchomione.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Wskazuje, że zadanie zakończyło się z powodu nieobsługiwanego wyjątku.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Wskazuje, że zadanie ukończone pomyślnie.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Wskazuje, że zadanie Zakończono wykonanie jego delegata niejawnie Trwa oczekiwanie na zakończenie dołączonych zadań podrzędnych.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące metody wewnętrznej są przydatne do aparat debugera, ponieważ ich oznaczenie wejścia do <xref:System.Threading.Tasks.Task> wykonanie kodu:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Zobacz także  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)