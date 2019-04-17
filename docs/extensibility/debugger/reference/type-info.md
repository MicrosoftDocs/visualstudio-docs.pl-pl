---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1b6af233b630b001d0d9087a2e7792497c2531d
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659942"
---
# <a name="typeinfo"></a>TYPE_INFO
Ta struktura określa różne rodzaje informacji na temat typu pola.

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

#### <a name="parameters"></a>Parametry
 wartość dwKind A [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) wyliczenie, które określa, jak interpretować Unii.

 type.typeMeta

 [C++ tylko] Zawiera [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struktury, jeśli `dwKind` jest `TYPE_KIND_METADATA`.

 type.typePdb

 [C++ tylko] Zawiera [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struktury, jeśli `dwKind` jest `TYPE_KIND_PDB`.

 type.typeBuilt

 [C++ tylko] Zawiera [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struktury, jeśli `dwKind` jest `TYPE_KIND_BUILT`.

 Dopełnienie nieużywane Type.unused.

 Wpisz nazwę Unii.

 unionmember

 [C# tylko] To typ odpowiednią strukturą ustalane na podstawie Marshal `dwKind`.

## <a name="remarks"></a>Uwagi
 Ta struktura jest przekazywany do [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metody, gdzie jest wypełnione. Sposób interpretowania zawartość struktury opiera się na `dwKind` pola.

> [!NOTE]
>  [C++ tylko] Jeśli `dwKind` jest równa `TYPE_KIND_BUILT`, jest zwolnić bazowego [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu, kiedy niszczenie `TYPE_INFO` struktury. Jest to realizowane przez wywołanie `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 [C# tylko] W poniższej tabeli przedstawiono, jak interpretować `unionmember` składowej dla każdego rodzaju typu. W przykładzie pokazano, jak to zrobić dla jednego rodzaju.

|`dwKind`|`unionmember` interpretowane jako|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak interpretować `unionmember` członkiem `TYPE_INFO` struktury w języku C#. W tym przykładzie interpretowanie tylko jeden typ (`TYPE_KIND_METADATA`), ale inne są interpretowane w taki sam sposób.

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

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)