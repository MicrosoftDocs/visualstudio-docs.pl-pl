---
title: Task, klasa — składowe wewnętrzne | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 200b35e60d3d468a934565959629298e6c6f04bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804871"
---
# <a name="task-class---internal-members"></a>Task, klasa — składowe wewnętrzne
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tym temacie opisano wewnętrznych członków <xref:System.Threading.Tasks.Task?displayProperty=fullName> klasy, które pomagają implementacji niestandardowego debugera. Aby uzyskać ogólne informacje dotyczące tej klasy, zobacz <xref:System.Threading.Tasks.Task> temat referencyjny.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tych wewnętrznych składowych z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Wskazuje, że zadanie zostało anulowane przed osiągnięciem uruchomiona lub jej anulowania potwierdzone i ukończone bez wyjątku zadania.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Wskazuje, że zadanie jest uruchomione.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Wskazuje, że zadanie zakończyło się z powodu nieobsługiwanego wyjątku.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Wskazuje, że zadanie ukończone pomyślnie.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Wskazuje, że zadanie zostało zakończone, wykonywanie jej delegata niejawnie Trwa oczekiwanie na zakończenie zadań podrzędnych dołączonych.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące metody wewnętrznej są przydatne do aparat debugera, ponieważ ich oznaczenie wejścia do <xref:System.Threading.Tasks.Task> wykonanie kodu:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
