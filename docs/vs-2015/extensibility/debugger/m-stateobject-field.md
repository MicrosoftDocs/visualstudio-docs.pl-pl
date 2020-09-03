---
title: m_stateObject pole | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e9cfc6f689504bef2a8366f90282641d1e9e105
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149053"
---
# <a name="m_stateobject-field"></a>m_stateObject, pole
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Obiekt reprezentujący dane, które będą używane przez tę akcję.  
  
 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z .NET Framework, następująca składnia jest dostępna w typowym języku pośrednim (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Uwagi  
 Jest to `state` parametr w <xref:System.Threading.Tasks.Task.%23ctor%2A> konstruktorze. Jest to również pole zapasowe dla <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Task, klasa](../../extensibility/debugger/task-class-internal-members.md)
