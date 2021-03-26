---
description: Opisuje metodę lub wywołanie funkcji.
title: CODE_PATH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b3e061fa0a9d6eb508e3085832007712cb6e434
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096515"
---
# <a name="code_path"></a>CODE_PATH
Opisuje metodę lub wywołanie funkcji.

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagCODE_PATH { 
    BSTR                bstrName;
    IDebugCodeContext2* pCode;
} CODE_PATH;
```

```csharp
public struct CODE_PATH {
    public string            bstrName;
    public IDebugCodeContext pCode;
}
```

## <a name="members"></a>Elementy członkowskie
`bstrName`\
Nazwa ścieżki kodu.

`pCode`\
Obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , który określa, gdzie w kodzie mają być wkroczenie do funkcji.

## <a name="remarks"></a>Uwagi
Ta struktura służy do implementowania funkcji krok po kroku. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) zwraca wszystkie wywołania z bieżącej lokalizacji w debugowanym programie. Ta struktura reprezentuje jedno takie wywołanie.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
