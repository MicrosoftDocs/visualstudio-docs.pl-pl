---
title: SetNotificationForWaitCompletion — Metoda | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 874e31c331f16e760e030f337dda715473b77af8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423403"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion, metoda
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia lub czyści bit stanu TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
## <a name="syntax"></a>Składnia  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parametry  
 `enabled`  
  
 `true` Aby ustawić bit; `false` w celu nieustawienia bitu.  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Debuger ustawia ten bit, aby ułatwić wyjście z metody asynchronicznej. Jeśli `enabled` jest `true` , ta metoda musi być wywoływana tylko w zadaniu, które nie zostało jeszcze ukończone. Jeśli `enabled` jest `false` , ta metoda może być wywoływana dla ukończonych zadań. W każdym z tych zdarzeń powinien być używany tylko w przypadku zadań w stylu obietnicy.  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też  
 [Task, klasa](../../extensibility/debugger/task-class-internal-members.md)
