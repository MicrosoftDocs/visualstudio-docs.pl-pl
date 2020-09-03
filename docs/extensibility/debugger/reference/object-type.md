---
title: OBJECT_TYPE | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714130"
---
# <a name="object_type"></a>OBJECT_TYPE
Określa typ obiektu z ewaluatora wyrażeń.

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
 Wskazuje, że obiekt jest wartością logiczną.

 `OBJECT_TYPE_CHAR`\
 Wskazuje, że obiekt jest znakiem.

 `OBJECT_TYPE_I1`\
 Wskazuje, że obiekt jest liczbą całkowitą ze znakiem jednobajtowym.

 `OBJECT_TYPE_U1`\
 Wskazuje, że obiekt jest liczbą całkowitą bez znaku.

 `OBJECT_TYPE_I2`\
 Wskazuje, że obiekt jest liczbą całkowitą ze znakiem dwubajtowym.

 `OBJECT_TYPE_U2`\
 Wskazuje, że obiekt jest dwubajtową liczbą całkowitą bez znaku.

 `OBJECT_TYPE_I4`\
 Wskazuje, że obiekt jest liczbą całkowitą ze znakiem czterech bajtów.

 `OBJECT_TYPE_U4`\
 Wskazuje, że obiekt jest liczbą całkowitą bez znaku z czterema bajtami.

 `OBJECT_TYPE_I8`\
 Wskazuje, że obiekt jest 8-bajtową liczbą całkowitą ze znakiem.

 `OBJECT_TYPE_U8`\
 Wskazuje, że obiekt jest 8-bajtową liczbą całkowitą bez znaku.

 `OBJECT_TYPE_R4`\
 Wskazuje, że obiekt jest liczbą zmiennoprzecinkową z czterema bajtami.

 `OBJECT_TYPE_R8`\
 Wskazuje, że obiekt jest liczbą zmiennoprzecinkową o ośmiu bajtach.

 `OBJECT_TYPE_OBJECT`\
 Wskazuje, że obiekt jest obiektem.

 `OBJECT_TYPE_NULL`\
 Wskazuje, że obiekt ma wartość NULL.

 `OBJECT_TYPE_CLASS`\
 Wskazuje, że obiekt jest klasą.

## <a name="remarks"></a>Uwagi
 Przeszedł jako argument do metod [Isprymitywobject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) i [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
