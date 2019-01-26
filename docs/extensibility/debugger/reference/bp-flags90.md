---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e81a384686303ecba2225dfcc865ae7f390664b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025308"
---
# <a name="bpflags90"></a>BP_FLAGS90
Wylicza prawidłowe wartości dla flagi opcjonalne. Flagi opcjonalne może służyć do określania dodatkowe informacje, gdy ustawisz punkt przerwania. To wyliczenie rozszerza [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 BP90_FLAG_NONE  
 Określa flagę nie punktu przerwania.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Określa, czy aparat debugowania (DE) powinny być mapowane punkt przerwania przy użyciu położenie dokumentu. Dotyczy tylko punkty przerwania ustawione w plikach źródłowych zorientowane na skrypt takie jak Active Server Pages (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Określa, że punkt przerwania mają być przetwarzane przez aparat debugowania, ale że aparat debugowania ostatecznie nie należy zatrzymywać oznacza to, że [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) obiektu zdarzenia nie powinny być przesyłane. Ta flaga ma służyć przede wszystkim z punktami śledzenia.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Używanego przez aparat debugowania natywnych, aby ustalić, czy stan przechodzenia krok po kroku powinno być wyczyszczone. Różni się od BP90_FLAG_DONT_STOP ponieważ BP90_FLAG_DONT_STOP nie jest ustawiona, jeśli punkt śledzenia wykonuje makra.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg90.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)