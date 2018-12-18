---
title: TaskScheduler, klasa — składowe wewnętrzne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a0f1306463abc9b8f025453f8b259014ba5de10
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774903"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler, klasa — składowe wewnętrzne
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tym temacie opisano wewnętrznych członków <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> klasy, które pomagają implementacji niestandardowego debugera. Aby uzyskać ogólne informacje dotyczące tej klasy, zobacz <xref:System.Threading.Tasks.TaskScheduler> temat referencyjny.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tych wewnętrznych składowych z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Pobiera tablicę wszystkich zaplanowanych zadań.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Pobiera tablicę wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiektów, które są aktualnie aktywne.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

