---
title: CODE_PATH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e09cd77308f83c2b9fb1b9cba70076ad797eb2e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62879225"
---
# <a name="codepath"></a>CODE_PATH
Opis wywołania metody lub funkcji.

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
bstrName nazwa ścieżki kodu.

pCode [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt, który identyfikuje gdzie kod w celu wkroczenia do funkcji.

## <a name="remarks"></a>Uwagi
Ta struktura jest używany do implementowania przechodzenie krok po kroku do funkcji. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) zwraca wszystkie wywołania z bieżącej lokalizacji w debugowanego programu. Ta struktura reprezentuje jedno takie wywołanie.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
