---
title: CONSTRUCTOR_ENUM | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: bd5067591f4f296825db6362f4a7b91f1a7a37e8
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412815"
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
crAll  
Wybiera wszystkie konstruktory.

crNonStatic  
Wybiera niestatycznych konstruktorów.

crStatic  
Wybiera konstruktorów statycznych.

## <a name="remarks"></a>Uwagi
Przekazywany jako argument do [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
