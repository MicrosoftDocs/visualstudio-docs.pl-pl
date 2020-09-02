---
title: NotifyDebuggerOfWaitCompletion — Metoda | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0548e1e791c41d806ccc222176ee571b037389
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153729"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion, metoda
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Metoda zastępcza używana jako docelowy punkt przerwania przez debuger. Ta metoda nie może być wbudowana ani zoptymalizowana.  
  
 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
## <a name="syntax"></a>Składnia  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie operacje Join z zadaniem powinny wywołać tę metodę, jeśli ustawiono bit powiadomień debugera.  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też  
 [Task, klasa](../../extensibility/debugger/task-class-internal-members.md)
