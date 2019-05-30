---
title: METADATA_TYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5aa21d4bfccd50e31c2fd7e76bb8808bba19bc58
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333748"
---
# <a name="metadatatype"></a>METADATA_TYPE
Ta struktura określa informacje o typie pola pobierana z metadanych.

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
 Identyfikator aplikacji, z którego pochodzą symbolu. Służy do jednoznacznego identyfikowania wystąpienia aplikacji.

 `guidModule`\
 Identyfikator GUID moduł, który zawiera tego pola.

 `tokClass`\
 Identyfikator tokenu metadanych tego typu.

 [C++] `_mdToken` jest `typedef` dla 32-bitowych `int`.

## <a name="remarks"></a>Uwagi
 Ta struktura jest wyświetlany jako część Unii w [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struktury, kiedy `dwKind` pole `TYPE_INFO` struktury jest ustawiona na `TYPE_KIND_METADATA` (wartość z zakresu od [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Wyliczenie).

 `tokClass` Wartość tokenu metadanych, który unikatowo identyfikuje typ. Aby uzyskać więcej informacji na temat sposobu interpretacji górny bity identyfikator tokenu metadanych, zobacz `CorTokenType` wyliczenia w pliku sekcję corhdr.h w [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] zestawu SDK.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)