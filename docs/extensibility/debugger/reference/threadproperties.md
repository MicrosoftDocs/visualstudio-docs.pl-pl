---
title: THREADPROPERTIES | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0e39102fa66c04a15042ffd82086ac66d3058ca
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316184"
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
 Kombinacja flag z [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) wyliczenie, opisujące, które pola w tej strukturze są prawidłowe.

 `dwThreadId`\
 Identyfikator wątku.

 `dwSuspendCount`\
 Wątek wstrzymania count.

 `dwThreadState`\
 Wartość z zakresu od [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) Wyliczenie wskazujące stan wątku operacyjne.

 `bstrPriority`\
 Ciąg określający priorytetu wątku; na przykład "Powyżej Normal", "Normal" lub "Czas krytyczne".

 `bstName`\
 Nazwa wątku.

 `bstrLocation`\
 Lokalizacja wątku (zazwyczaj ramki stosu najwyższego poziomu), zwykle wyrażona jako nazwa metody, w której obecnie wykonywanie zostało zatrzymane.

## <a name="remarks"></a>Uwagi
 Ta struktura jest wypełniane przez wywołanie [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metody. Informacje, więc zwracana jest zwykle używana w wypełnianie **wątków** okna.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)