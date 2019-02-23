---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f3efd78d5e3c84f9d23068be62efdf751767dd1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715072"
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
W tym artykule opisano różne rodzaje adresów.

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

## <a name="terms"></a>Warunki
wartość dwKind A [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia, określając sposób interpretowania Unii.

addr.addrNative

 [Tylko w języku C++] Zawiera [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) struktury, jeśli `dwKind` = ADDRESS_KIND_NATIVE.

addr.addrThisRel

 [Tylko w języku C++] Zawiera[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) struktury, jeśli `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

addr.addUPhysical

 [Tylko w języku C++] Zawiera[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) struktury, jeśli `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.

addr.addrMethod

 [Tylko w języku C++] Zawiera[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) struktury, jeśli `dwKind` = ADDRESS_KIND_METHOD.

addr.addrField

 [Tylko w języku C++] Zawiera[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) struktury, jeśli `dwKind` = ADDRESS_KIND_FIELD.

addr.addrLocal

 [Tylko w języku C++] Zawiera[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) struktury, jeśli `dwKind` = ADDRESS_KIND_LOCAL.

addr.addrParam

 [Tylko w języku C++] Zawiera[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) struktury, jeśli `dwKind` = ADDRESS_KIND_PARAM.

addr.addrArrayElem

 [Tylko w języku C++] Zawiera[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) struktury, jeśli `dwKind` = ADDRESS_KIND_ARRAYELEM.

addr.addrRetVal

 [Tylko w języku C++] Zawiera[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) struktury, jeśli `dwKind` = ADDRESS_KIND_RETVAL.

addr.unused

 Dopełnienie [C++ tylko].

addr

 [Tylko w języku C++] Nazwa Unii.

unionmember

 [C# tylko] Ta wartość musi być wprowadzane do typu odpowiednią strukturą na podstawie `dwKind`. Zobacz uwagi dla skojarzenia między `dwKind` i interpretacji Unii.

## <a name="remarks"></a>Uwagi
Ta struktura jest częścią [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury i reprezentuje jeden z wielu różnych rodzajów adresów ( `DEBUG_ADDRESS` struktury jest wypełniane przez wywołanie [getaddress —](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metody).


 [C# tylko] W poniższej tabeli przedstawiono, jak interpretować `unionmember` składowej dla każdego rodzaju adresu. W przykładzie pokazano, jak to zrobić dla jednego rodzaju adresu.

|`dwKind`|`unionmember` interpretowane jako|
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
W tym przykładzie pokazano, jak interpretować jeden rodzaj adresu (`METADATA_ADDRESS_ARRAYELEM`) z `DEBUG_ADDRESS_UNION` struktury w języku C#. Wszystkie pozostałe elementy mogą być interpretowane w taki sam sposób.

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

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
