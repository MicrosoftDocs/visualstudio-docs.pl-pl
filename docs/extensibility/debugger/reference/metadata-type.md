---
title: METADATA_TYPE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afe5ea128775c7be0e48035ab4c7e7d370c9d233
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714279"
---
# <a name="metadata_type"></a>METADATA_TYPE
Ta struktura określa informacje o typie pola pobranym z metadanych.

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
 Identyfikator aplikacji, z której pochodzi symbol. Służy do jednoznacznej identyfikacji wystąpienia aplikacji.

 `guidModule`\
 Identyfikator GUID modułu zawierającego to pole.

 `tokClass`\
 Identyfikator tokenu metadanych tego typu.

 [C++] `_mdToken` jest `typedef` dla 32-bitowego `int`.

## <a name="remarks"></a>Uwagi
 Ta struktura pojawia się jako część unii w [strukturze TYPE_INFO,](../../../extensibility/debugger/reference/type-info.md) gdy `dwKind` pole `TYPE_INFO` struktury jest ustawiona na `TYPE_KIND_METADATA` (wartość z [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) wyliczenia).

 Wartość `tokClass` jest token metadanych, który jednoznacznie identyfikuje typ. Aby uzyskać szczegółowe informacje na temat interpretowania górnych bitów `CorTokenType` identyfikatora tokenu metadanych, zobacz wyliczenie w pliku corhdr.h w pliku .NET Framework SDK.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
