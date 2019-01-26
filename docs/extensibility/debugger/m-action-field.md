---
title: Pole m_action | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efe8e9f09a76cc32b7a6d188d980c53e14fd34a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966793"
---
# <a name="maction-field"></a>pole m_action
Delegat, który reprezentuje kod do wykonania w <xref:System.Threading.Tasks.Task> obiektu.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w *mscorlib.dll*)  
  
 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
.field assembly object m_action  
```  
  
## <a name="remarks"></a>Uwagi  
 Jest to `action` parametru w <xref:System.Threading.Tasks.Task.%23ctor%2A> konstruktora.  
  
## <a name="see-also"></a>Zobacz także  
 [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)