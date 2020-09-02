---
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c17564c992f4c8855d8a96165975a5d0e132755c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547211"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa typ komunikatu i przyczynę.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Wskazuje, że wiadomość powinna zostać wysłana do okna danych wyjściowych. Jest to wzajemnie wykluczające się z `MT_MESSAGEBOX` .  
  
 MT_MESSAGEBOX  
 Wskazuje, że komunikat powinien być wyświetlany w oknie komunikatu. Jest to wzajemnie wykluczające się z `MT_OUTPUTSTRING` .  
  
 MT_TYPE_MASK  
 Wartość maski służąca do izolowania miejsca docelowego wiadomości.  
  
 MT_REASON_EXCEPTION  
 Wskazuje, że w wyniku wyjątku zostanie wyświetlone okno komunikatu. Jest to wzajemnie wykluczające się z `MT_REASON_TRACEPOINT` .  
  
 MT_REASON_TRACEPOINT  
 Wskazuje, że okno komunikatu jest wyświetlane w wyniku naciśnięcia punkt śledzenia. Jest to wzajemnie wykluczające się z `MT_REASON_EXCEPTION` .  
  
 MT_REASON_MASK  
 Wartość maski służąca do oddzielenia przyczyny wyświetlania komunikatu.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są zwracane z metod [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) i [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .  
  
 Jedną z wartości przyczyn można łączyć z jedną z wyjściowych wartości docelowych przy użyciu bitowej `OR` .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
