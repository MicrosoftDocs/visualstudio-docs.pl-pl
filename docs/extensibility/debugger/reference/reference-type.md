---
title: REFERENCE_TYPE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ce6ad17aa32b98fd28914c422a49bd8bcc14b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713658"
---
# <a name="reference_type"></a>REFERENCE_TYPE
Określa typ odwołania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
typedef DWORD REFERENCE_TYPE;
```

```csharp
public enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
```

## <a name="fields"></a>Pola
 `REF_TYPE_WEAK`\
 Określa słabe odniesienie. Nie można `REF_TYPE_STRONG`łączyć z plikem .

 `REF_TYPE_STRONG`\
 Określa silne odniesienie. Nie można `REF_TYPE_WEAK`łączyć z plikem .

## <a name="remarks"></a>Uwagi
 Używany jako `dwRefType` element [członkowski](../../../extensibility/debugger/reference/debug-reference-info.md) DEBUG_REFERENCE_INFO struktury.

 Przekazany jako parametr do [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md) metody.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)
