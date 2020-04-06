---
title: BUILT_TYPE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 885f17b0841a39672c87be5bc7c947b2e0d9c7e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737697"
---
# <a name="built_type"></a>BUILT_TYPE
Ta struktura określa informacje o typie pola pobranym z metadanych.

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
Identyfikator aplikacji, z której pochodzi symbol. Służy do jednoznacznej identyfikacji wystąpienia aplikacji.

`guidModule`\
Identyfikator GUID modułu zawierającego to pole.

`pUnderlyingField`\
Obiekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) identyfikujący pole bazowe skojarzone z tym utworzonym polem.

## <a name="remarks"></a>Uwagi
Ta struktura pojawia się jako część unii w [strukturze TYPE_INFO,](../../../extensibility/debugger/reference/type-info.md) gdy `dwKind` pole `TYPE_INFO` struktury jest ustawiona na `TYPE_KIND_BUILT` (wartość z [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) wyliczenia).

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
