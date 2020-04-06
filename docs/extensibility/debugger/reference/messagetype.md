---
title: TYP WIADOMOŚCI | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714501"
---
# <a name="messagetype"></a>MESSAGETYPE
Określa typ i przyczynę wiadomości.

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
 Wskazuje, że wiadomość powinna zostać wysłana do okna danych wyjściowych. To wzajemnie się `MT_MESSAGEBOX`wyklucza z .

 `MT_MESSAGEBOX`\
 Wskazuje, że wiadomość powinna być wyświetlana w oknie komunikatu. To wzajemnie się `MT_OUTPUTSTRING`wyklucza z .

 `MT_TYPE_MASK`\
 Wartość maski do wyizolowania miejsca docelowego dla wiadomości.

 `MT_REASON_EXCEPTION`\
 Wskazuje, że okno komunikatu jest wyświetlane w wyniku wyjątku. To wzajemnie się `MT_REASON_TRACEPOINT`wyklucza z .

 `MT_REASON_TRACEPOINT`\
 Wskazuje, że okno komunikatu jest wyświetlane w wyniku trafienia w punkt śledzenia. To jest wzajemnie `MT_REASON_EXCEPTION`się wykluczają .

 `MT_REASON_MASK`\
 Wartość maski do wyizolowania przyczyny wyświetlenia wiadomości.

## <a name="remarks"></a>Uwagi
 Te wartości są zwracane z [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) i [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) metody.

 Jedną z wartości przyczyny można połączyć z jedną z `OR`wyjściowych wartości docelowych za pomocą bitowego .

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
