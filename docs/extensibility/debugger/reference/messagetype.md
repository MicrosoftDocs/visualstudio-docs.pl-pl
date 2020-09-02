---
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d0fd12495a59427500c16ef6f37d9f8b6e61f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714501"
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

## <a name="fields"></a>Pola
 `MT_OUTPUTSTRING`\
 Wskazuje, że wiadomość powinna zostać wysłana do okna danych wyjściowych. Jest to wzajemnie wykluczające się z `MT_MESSAGEBOX` .

 `MT_MESSAGEBOX`\
 Wskazuje, że komunikat powinien być wyświetlany w oknie komunikatu. Jest to wzajemnie wykluczające się z `MT_OUTPUTSTRING` .

 `MT_TYPE_MASK`\
 Wartość maski służąca do izolowania miejsca docelowego wiadomości.

 `MT_REASON_EXCEPTION`\
 Wskazuje, że w wyniku wyjątku zostanie wyświetlone okno komunikatu. Jest to wzajemnie wykluczające się z `MT_REASON_TRACEPOINT` .

 `MT_REASON_TRACEPOINT`\
 Wskazuje, że okno komunikatu jest wyświetlane w wyniku naciśnięcia punkt śledzenia. Jest to wzajemnie wykluczające się z `MT_REASON_EXCEPTION` .

 `MT_REASON_MASK`\
 Wartość maski służąca do oddzielenia przyczyny wyświetlania komunikatu.

## <a name="remarks"></a>Uwagi
 Te wartości są zwracane z metod [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) i [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .

 Jedną z wartości przyczyn można łączyć z jedną z wyjściowych wartości docelowych przy użyciu bitowej `OR` .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
