---
title: TYPE_INFO | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713328"
---
# <a name="type_info"></a>TYPE_INFO
Ta struktura określa różne rodzaje informacji o typie pola.

## <a name="syntax"></a>Składnia

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>Elementy członkowskie
 `dwKind`\
 Wartość z [wyliczenia dwTYPE_KIND,](../../../extensibility/debugger/reference/dwtype-kind.md) która określa sposób interpretowania unii.

 `type.typeMeta`\
 [Tylko C++] Zawiera [strukturę METADATA_TYPE,](../../../extensibility/debugger/reference/metadata-type.md) `dwKind` `TYPE_KIND_METADATA`jeśli jest .

 `type.typePdb`\
 [Tylko C++] Zawiera [strukturę PDB_TYPE,](../../../extensibility/debugger/reference/pdb-type.md) `dwKind` jeśli `TYPE_KIND_PDB`jest .

 `type.typeBuilt`\
 [Tylko C++] Zawiera [strukturę BUILT_TYPE,](../../../extensibility/debugger/reference/built-type.md) `dwKind` jeśli `TYPE_KIND_BUILT`jest .

 `type.unused`\
 Nieużywane dopełnienie.

 `type`\
 Nazwa związku.

 `unionmember`\
 [Tylko C#] Marszałek to do odpowiedniego `dwKind`typu struktury w oparciu o .

## <a name="remarks"></a>Uwagi
 Ta struktura jest przekazywana do [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metody, gdzie jest wypełniona. Sposób interpretowania zawartości struktury zależy od `dwKind` pola.

> [!NOTE]
> [Tylko C++] Jeśli `dwKind` jest `TYPE_KIND_BUILT`równa , a następnie należy zwolnić podstawowy [obiekt IDebugField](../../../extensibility/debugger/reference/idebugfield.md) podczas niszczenia `TYPE_INFO` struktury. Odbywa się to `typeInfo.type.typeBuilt.pUnderlyingField->Release()`poprzez wywołanie .

 [Tylko C#] W poniższej tabeli `unionmember` pokazano, jak interpretować element członkowski dla każdego typu. Przykład pokazuje, jak to zrobić dla jednego rodzaju typu.

|`dwKind`|`unionmember`interpretowane jako|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Przykład
 W tym przykładzie `unionmember` pokazano, `TYPE_INFO` jak interpretować element członkowski struktury w języku C#. W tym przykładzie pokazano`TYPE_KIND_METADATA`interpretację tylko jednego typu ( ), ale pozostałe są interpretowane w dokładnie taki sam sposób.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
            }
        }
    }
}
```

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
