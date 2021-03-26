---
description: Struktura BUILT_TYPE określa informacje o typie pola pobieranym z metadanych.
title: BUILT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00a031d02bba7ffcc1dca6f2cf73cfceeed04838
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096580"
---
# <a name="built_type"></a>BUILT_TYPE
Ta struktura określa informacje o typie pola pobieranym z metadanych.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Elementy członkowskie
`ulAppDomainID`\
Identyfikator aplikacji, z której pochodzi symbol. Służy do jednoznacznego identyfikowania wystąpienia aplikacji.

`guidModule`\
Identyfikator GUID modułu zawierającego to pole.

`pUnderlyingField`\
Obiekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , który identyfikuje podstawowe pole skojarzone z tym skompilowanym polem.

## <a name="remarks"></a>Uwagi
Ta struktura jest wyświetlana jako część Unii w strukturze [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) , gdy `dwKind` pole `TYPE_INFO` struktury jest ustawione na `TYPE_KIND_BUILT` (wartość z wyliczenia [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

## <a name="requirements"></a>Wymagania
Nagłówek: sh. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
