---
title: GetTaskSchedulersForDebugger — Metoda | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 995bf40669a4480f6f1ddfe8071a7885a4659c9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152714"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger, metoda
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera tablicę wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiektów, które są obecnie aktywne.  
  
 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z .NET Framework, następująca składnia jest dostępna w typowym języku pośrednim (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Tablica wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiektów, które są obecnie aktywne w tym elemencie <xref:System.AppDomain> .  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest bezpieczna wątkowo i nie należy jej używać jednocześnie z innymi wystąpieniami <xref:System.Threading.Tasks.TaskScheduler> . Powinien być wywoływany z debugera tylko wtedy, gdy debuger wstrzymał wszystkie pozostałe wątki.  
  
## <a name="see-also"></a>Zobacz też  
 [TaskScheduler, klasa](../../extensibility/debugger/taskscheduler-class-internal-members.md)
