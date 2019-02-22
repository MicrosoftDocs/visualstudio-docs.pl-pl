---
title: CONSTRUCTOR_ENUM | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb880516d13085af594bb639a15d76fca8262279
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680363"
---
# <a name="constructorenum"></a>CONSTRUCTOR_ENUM
Zaznacza różne rodzaje konstruktorów.

## <a name="syntax"></a>Składnia

```cpp
typedef enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
} CONSTRUCTOR_ENUM;
```

```csharp
public enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
};
```

## <a name="members"></a>Elementy członkowskie
crAll wybiera wszystkie konstruktory.

crNonStatic wybiera niestatycznych konstruktorów.

crStatic wybiera konstruktorów statycznych.

## <a name="remarks"></a>Uwagi
Przekazywany jako argument do [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
