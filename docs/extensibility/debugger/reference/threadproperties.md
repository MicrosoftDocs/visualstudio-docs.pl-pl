---
title: THREADPROPERTIES | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0ed4e33b1f8e0e905f3c88493c9f513c177fbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713422"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Opisuje właściwości wątku.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagTHREADPROPERTIES { 
   THREADPROPERTY_FIELDS dwFields;
   DWORD                 dwThreadId;
   DWORD                 dwSuspendCount;
   DWORD                 dwThreadState;
   BSTR                  bstrPriority;
   BSTR                  bstrName;
   BSTR                  bstrLocation;
} THREADPROPERTIES;
```

```csharp
public struct THREADPROPERTIES { 
   public uint   dwFields;
   public uint   dwThreadId;
   public uint   dwSuspendCount;
   public uint   dwThreadState;
   public string bstrPriority;
   public string bstrName;
   public string bstrLocation;
};
```

## <a name="members"></a>Elementy członkowskie
 `dwFields`\
 Kombinacja flag z wyliczenia [THREADPROPERTY_FIELDS,](../../../extensibility/debugger/reference/threadproperty-fields.md) opisująca pola w tej strukturze są prawidłowe.

 `dwThreadId`\
 Identyfikator wątku.

 `dwSuspendCount`\
 Liczba wstrzymania wątku.

 `dwThreadState`\
 Wartość z [wyliczenia THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) wskazująca stan wątku roboczego.

 `bstrPriority`\
 Ciąg określający priorytet wątku; na przykład "Powyżej normy", "Normalny" lub "Czas krytyczny".

 `bstName`\
 Nazwa wątku.

 `bstrLocation`\
 Lokalizacja wątku (zwykle najwyższej ramki stosu), zazwyczaj wyrażona jako nazwa metody, w której wykonanie jest obecnie zatrzymane.

## <a name="remarks"></a>Uwagi
 Ta struktura jest wypełniona przez wywołanie [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metody. Informacje tak zwrócone jest zwykle używane w wypełnianiu **wątków** okna.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
