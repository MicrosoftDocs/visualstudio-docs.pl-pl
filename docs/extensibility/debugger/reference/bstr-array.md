---
description: Struktura opisująca tablicę ciągów.
title: BSTR_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5fb882bb31f6fd525d00dc134e042e9bce9398f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170975"
---
# <a name="bstr_array"></a>BSTR_ARRAY
Struktura opisująca tablicę ciągów.

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagBSTR_ARRAY {
    DWORD dwCount;
    BSTR* Members;
} BSTR_ARRAY;
```

```csharp
struct BSTR_ARRAY {
    DWORD    dwCount;
    string[] Members;
}
```

## <a name="members"></a>Elementy członkowskie
`dwCount`\
Liczba ciągów w `Members` tablicy.

`Members`\
Tablica ciągów.

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracana z metody [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) .

 [Tylko C++] Każdy pojedynczy ciąg musi być zwolniony przy użyciu `SysFreeString` , a `Members` Tablica musi być zwolniona z `CoTaskMemFree` .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
