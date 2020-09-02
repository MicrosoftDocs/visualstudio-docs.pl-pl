---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e6ee00402c13b2a79e4e6757a127211eda9c3c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149389"
---
# <a name="evalflags"></a>EVALFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa flagi kontrolujące Obliczanie wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>Elementy członkowskie  
 EVAL_RETURNVALUE  
 Określa, że wartość zwracana, jeśli ma zostać obliczona.  
  
 EVAL_NOSIDEEFFECTS  
 Określa, że efekty uboczne nie są dozwolone.  
  
 EVAL_ALLOWBPS  
 Określa zatrzymanie dla punktów przerwania.  
  
 EVAL_ALLOWERRORREPORT  
 Określa, że raportowanie błędów ma być dozwolone dla hosta. Służy głównie do oceny wyrażeń w skrypcie w programie Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Wymusza, aby funkcje były oceniane jako adresy zamiast wywoływania funkcji.  
  
 EVAL_NOFUNCEVAL  
 Zapobiega ocenie funkcji. Rozważmy na przykład `int` token w wyrażeniu `myExpression(int) + 10` . Ta funkcja może być poprawnie oceniona jako adres, ale nie jako wartość.  
  
 EVAL_NOEVENTS  
 Flaga wskazująca, że zdarzenia występujące podczas obliczania wyrażenia nie powinny być wysyłane do Menedżera debugowania sesji (SDM) ani do IDE.  
  
## <a name="remarks"></a>Uwagi  
 Flagi te są przenoszone jako argumenty do metod [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) i [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) .  
  
 Flagi te mogą być połączone z bitowym lub.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
