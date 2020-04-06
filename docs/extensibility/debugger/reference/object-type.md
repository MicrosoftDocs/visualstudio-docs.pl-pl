---
title: OBJECT_TYPE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ffb85a14e42dd57c345481285eb1f776b3866d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714130"
---
# <a name="object_type"></a>OBJECT_TYPE
Określa typ obiektu od oceniającego wyrażenie.

## <a name="syntax"></a>Składnia

```cpp
enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
typedef DWORD OBJECT_TYPE;
```

```csharp
public enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
```

## <a name="fields"></a>Pola
 `OBJECT_TYPE_BOOLEAN`\
 Wskazuje, że obiekt jest wartościowym.

 `OBJECT_TYPE_CHAR`\
 Wskazuje, że obiekt jest znakiem.

 `OBJECT_TYPE_I1`\
 Wskazuje, że obiekt jest jedną ą ćdemotwą podpisaną całkowitej.

 `OBJECT_TYPE_U1`\
 Wskazuje, że obiekt jest jedno bajtową niepodpisaną całkowitej liczby.

 `OBJECT_TYPE_I2`\
 Wskazuje, że obiekt jest dwu bajtową podpisaną kreśliącą.

 `OBJECT_TYPE_U2`\
 Wskazuje, że obiekt jest dwu bajtową niepodpisaną całkowitej liczby.

 `OBJECT_TYPE_I4`\
 Wskazuje, że obiekt jest 4-bajtową podpisaną kreślić.

 `OBJECT_TYPE_U4`\
 Wskazuje, że obiekt jest cztero bajtową niepodpisaną całkowitej liczby.

 `OBJECT_TYPE_I8`\
 Wskazuje, że obiekt jest 8-bajtową podpisaną kreśliń integer.

 `OBJECT_TYPE_U8`\
 Wskazuje, że obiekt jest 8-bajtową niepodpisaną całkowitej liczby.

 `OBJECT_TYPE_R4`\
 Wskazuje, że obiekt jest cztero bajtową liczbą zmiennoprzecinkową.

 `OBJECT_TYPE_R8`\
 Wskazuje, że obiekt jest ośmioma-bajtową liczbą zmiennoprzecinkową.

 `OBJECT_TYPE_OBJECT`\
 Wskazuje, że obiekt jest obiektem.

 `OBJECT_TYPE_NULL`\
 Wskazuje, że obiekt ma wartość NULL.

 `OBJECT_TYPE_CLASS`\
 Wskazuje, że obiekt jest klasą.

## <a name="remarks"></a>Uwagi
 Przekazany jako argument do [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) i [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) metody.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
