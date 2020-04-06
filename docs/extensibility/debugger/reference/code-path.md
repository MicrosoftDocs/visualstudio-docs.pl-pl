---
title: CODE_PATH | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3148b75e56b61ee545c6bc82b972c13572199af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737669"
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
[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt, który identyfikuje, gdzie w kodzie, aby przejść do funkcji.

## <a name="remarks"></a>Uwagi
Ta struktura jest używana do implementacji przechodzenia do funkcji. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) zwraca wszystkie wywołania z bieżącej lokalizacji w debugowanym programie. Ta struktura reprezentuje jedno takie wywołanie.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
