---
title: Metoda NotifyDebuggerOfWaitCompletion | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf89c21d533ae994052d9bf47c9f6e2b3d480921
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944577"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Metoda NotifyDebuggerOfWaitCompletion
Metoda symbolu zastępczego używany jako obiekt docelowy punkt przerwania przez debuger. Ta metoda nie może być śródwierszowa lub zoptymalizowane.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w *mscorlib.dll*)  
  
## <a name="syntax"></a>Składnia  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie operacje łączenia z zadaniem powinna wywołać tę metodę, jeśli ustawiono bit powiadomienia ich debugera.  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz także  
 [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)