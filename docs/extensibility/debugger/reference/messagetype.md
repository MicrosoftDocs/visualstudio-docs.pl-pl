---
title: MESSAGETYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35a75bc824e5e0e677f4b1b5e2afaea97707231f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949687"
---
# <a name="messagetype"></a>MESSAGETYPE
Określa typ komunikatu i przyczynę.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 MT_OUTPUTSTRING  
 Wskazuje, że w oknie danych wyjściowych powinna zostać wysłana wiadomość. To jest wzajemnie wykluczających się z `MT_MESSAGEBOX`.  
  
 MT_MESSAGEBOX  
 Wskazuje, że komunikat powinien być wyświetlany w oknie komunikatu. To jest wzajemnie wykluczających się z `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 Wartość maski do izolowania miejsce docelowe dla wiadomości.  
  
 MT_REASON_EXCEPTION  
 Wskazuje, że okno komunikatu jest pokazywane w wyniku wystąpienia wyjątku. To jest wzajemnie wykluczających się z `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Wskazuje, że okno komunikatu jest pokazywane w wyniku osiągnięcia punkt śledzenia. To jest wzajemnie wykluczających się do `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 Wartość maski do izolowania Przyczyna wiadomości są wyświetlane.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są zwracane z [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) i [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) metody.  
  
 Jedna z wartości Przyczyna może być łączone z jedną z wartości docelowe danych wyjściowych za pomocą bitowej `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)