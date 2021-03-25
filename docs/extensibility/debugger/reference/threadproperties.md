---
description: Opisuje właściwości wątku.
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0707cb5da4c63ffd686f22fa691c103c954478c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070859"
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
 Kombinacja flag z wyliczenia [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , opisująca, które pola w tej strukturze są prawidłowe.

 `dwThreadId`\
 Identyfikator wątku.

 `dwSuspendCount`\
 Liczba wstrzymań wątku.

 `dwThreadState`\
 Wartość z wyliczenia [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) wskazująca stan wątku operacyjnego.

 `bstrPriority`\
 Ciąg określający priorytet wątku; na przykład "powyżej normalnego", "normalny" lub "czas krytyczne".

 `bstName`\
 Nazwa wątku.

 `bstrLocation`\
 Lokalizacja wątku (zazwyczaj ramka najwyższego stosu), zwykle wyrażona jako nazwa metody, w której wykonywanie jest aktualnie zatrzymane.

## <a name="remarks"></a>Uwagi
 Ta struktura jest wypełniana przez wywołanie metody [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) . Te informacje są zwykle używane do wypełniania okna **wątki** .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
