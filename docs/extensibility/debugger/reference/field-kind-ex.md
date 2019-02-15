---
title: FIELD_KIND_EX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28a880af0a5d691a57e32b22f9f7823cca45827d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317786"
---
# <a name="fieldkindex"></a>FIELD_KIND_EX
Wylicza dodatkowe rodzajów pól, które [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt może zawierać. To wyliczenie rozszerza [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
typedef DWORD FIELD_KIND_EX;
```

```csharp
public enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
```

## <a name="members"></a>Elementy członkowskie
FIELD_KIND_EX_NONE  
Pole nie zawiera typie rozszerzonym.

FIELD_TYPE_EX_METHODVAR  
Pole zawiera zmienną metody.

FIELD_TYPE_EX_CLASSVAR  
Pole zawiera zmienną klasy.

## <a name="requirements"></a>Wymagania
Nagłówek: Sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
