---
description: Struktura METADATA_TYPE określa informacje o typie pola pobieranym z metadanych.
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a76e051e146985338564d497323b6232b35a4a1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079855"
---
# <a name="metadata_type"></a>METADATA_TYPE
Ta struktura określa informacje o typie pola pobieranym z metadanych.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Parametry
 `ulAppDomainID`\
 Identyfikator aplikacji, z której pochodzi symbol. Służy do jednoznacznego identyfikowania wystąpienia aplikacji.

 `guidModule`\
 Identyfikator GUID modułu zawierającego to pole.

 `tokClass`\
 Identyfikator tokenu metadanych tego typu.

 [C++] `_mdToken` jest `typedef` dla 32-bitowej `int` .

## <a name="remarks"></a>Uwagi
 Ta struktura jest wyświetlana jako część Unii w strukturze [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) , gdy `dwKind` pole `TYPE_INFO` struktury jest ustawione na `TYPE_KIND_METADATA` (wartość z wyliczenia [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

 `tokClass`Wartość jest tokenem metadanych, który jednoznacznie identyfikuje typ. Aby uzyskać szczegółowe informacje na temat interpretowania górnych bitów identyfikatora tokenu metadanych, zapoznaj się z `CorTokenType` wyliczeniem w pliku corhdr. h w zestawie SDK .NET Framework.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
