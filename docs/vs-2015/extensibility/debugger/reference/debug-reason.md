---
title: DEBUG_REASON | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ff97c4ffeac4b25aa92da3213525ad35ae444a3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801280"
---
# <a name="debugreason"></a>DEBUG_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, dlaczego ten proces został uruchomiony dla debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 DEBUG_REASON_ERROR  
 Wystąpił błąd nieokreślonym (są one używane jako domyślne warunku, gdy żaden z innych powodów, dla których Dopasuj).  
  
 DEBUG_REASON_USER_LAUNCHED  
 Proces został uruchomiony na żądanie użytkownika.  
  
 DEBUG_REASON_USER_ATTACHED  
 Proces działa już został dołączony do przez użytkownika.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 Proces został dołączony do automatycznie, podczas jej uruchamiania.  
  
 DEBUG_REASON_CAUSALITY  
 Proces został uruchomiony ze względu na *Just-In-Time* zdarzenia debugowania (JIT).  
  
## <a name="remarks"></a>Uwagi  
 Zwrócone w wyniku [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

