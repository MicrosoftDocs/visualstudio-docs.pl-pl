---
title: DEBUG_ADDRESS_UNION | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad531ee10914e404459632c98aae4a9bbda8e437
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737524"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Opisuje różne rodzaje adresów.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Elementy członkowskie
`dwKind`\
Wartość z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia, określając, jak interpretować unii.

`addr.addrNative`\
[Tylko C++] Zawiera [strukturę NATIVE_ADDRESS,](../../../extensibility/debugger/reference/native-address.md) jeśli `dwKind` = ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[Tylko C++] Zawiera[strukturę UNMANAGED_ADDRESS_THIS_RELATIVE,](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) `dwKind` jeśli = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[Tylko C++] Zawiera[strukturę UNMANAGED_ADDRESS_PHYSICAL,](../../../extensibility/debugger/reference/unmanaged-address-physical.md) `dwKind` jeśli = ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[Tylko C++] Zawiera[strukturę METADATA_ADDRESS_METHOD,](../../../extensibility/debugger/reference/metadata-address-method.md) jeśli `dwKind` = ADDRESS_KIND_METHOD.

`addr.addrField`\
[Tylko C++] Zawiera[strukturę METADATA_ADDRESS_FIELD,](../../../extensibility/debugger/reference/metadata-address-field.md) `dwKind` jeśli = ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[Tylko C++] Zawiera[strukturę METADATA_ADDRESS_LOCAL,](../../../extensibility/debugger/reference/metadata-address-local.md) `dwKind` jeśli = ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[Tylko C++] Zawiera[strukturę METADATA_ADDRESS_PARAM,](../../../extensibility/debugger/reference/metadata-address-param.md) `dwKind` jeśli = ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[Tylko C++] Zawiera[strukturę METADATA_ADDRESS_ARRAYELEM,](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) `dwKind` jeśli = ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[Tylko C++] Zawiera[strukturę METADATA_ADDRESS_RETVAL,](../../../extensibility/debugger/reference/metadata-address-retval.md) `dwKind` jeśli = ADDRESS_KIND_RETVAL.

`addr.unused`\
Dopełnienie [tylko C++].

`addr`\
[Tylko C++] Nazwa związku.

`unionmember`\
[Tylko C#] Wartość ta musi być zorganizowana do odpowiedniego `dwKind`typu struktury na podstawie . Patrz Uwagi dotyczące związku `dwKind` i interpretacji związku.

## <a name="remarks"></a>Uwagi
Ta struktura jest częścią [struktury DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) i reprezentuje jeden z wielu różnych `DEBUG_ADDRESS` rodzajów adresów (struktura jest wypełniona wywołaniem [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metody).

 [Tylko C#] W poniższej tabeli `unionmember` przedstawiono sposób interpretowania elementu członkowskiego dla każdego rodzaju adresu. Przykład pokazuje, jak to zrobić dla jednego rodzaju adresu.

|`dwKind`|`unionmember`interpretowane jako|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Przykład
W tym przykładzie pokazano, jak`METADATA_ADDRESS_ARRAYELEM`interpretować `DEBUG_ADDRESS_UNION` jeden rodzaj adresu ( ) struktury w języku C#. Pozostałe elementy mogą być interpretowane w dokładnie taki sam sposób.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
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
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
