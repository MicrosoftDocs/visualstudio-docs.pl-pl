---
title: ADDRESS_KIND | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1298df79bbe34b240d6e7b186f42e20b3d1a89de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738149"
---
# <a name="address_kind"></a>ADDRESS_KIND
Określa rodzaje adresów.

## <a name="syntax"></a>Składnia

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>Pola
`ADDRESS_KIND_NATIVE`\
Adres macierzysty, reprezentowany przez [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) strukturę.

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Niezarządzany adres względem `this` `Me` (w języku Visual Basic) wskaźnik i reprezentowane przez [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) struktury.

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
Niezarządzany adres fizyczny, reprezentowany przez [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) strukturę.

`ADDRESS_KIND_METHOD`\
Metoda klasy, reprezentowana przez [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) strukturę.

`ADDRESS_KIND_FIELD`\
Pole klasy, reprezentowane przez [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) strukturę.

`ADDRESS_KIND_LOCAL`\
Adres jest dla zmiennej lokalnej i jest reprezentowany przez [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) struktury.

`ADDRESS_KIND_PARAM`\
Metoda lub parametr funkcji, reprezentowany przez [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) strukturę.

`ADDRESS_KIND_ARRAYELEM`\
Element tablicy, reprezentowany przez [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) strukturę.

`ADDRESS_KIND_RETVAL`\
Wartość zwracana, reprezentowana przez [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) strukturę.

## <a name="remarks"></a>Uwagi
[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) Metoda zwraca [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury, która zawiera jedność możliwych struktur, [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struktury. Pole `dwKind` `DEBUG_ADDRESS_UNION` struktury przechowuje `ADDRESS_KIND` wartość i opisuje sposób interpretowania pola unii.

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
