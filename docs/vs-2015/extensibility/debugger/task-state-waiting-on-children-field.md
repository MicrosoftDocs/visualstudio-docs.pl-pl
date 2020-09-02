---
title: TASK_STATE_WAITING_ON_CHILDREN pole | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2dfb7ca683b7a05151539feda92a2575197b189
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176712"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN, pole
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zadanie zakończyło wykonywanie delegata i nieoczekiwanie oczekuje na ukończenie dołączonych zadań podrzędnych.  
  
 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z .NET Framework, następująca składnia jest dostępna w typowym języku pośrednim (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli pole [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) zawiera tę wartość, <xref:System.Threading.Tasks.Task.Status%2A> Właściwość zwraca <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .  
  
## <a name="see-also"></a>Zobacz też  
 [Task, klasa](../../extensibility/debugger/task-class-internal-members.md)
