---
title: BSTR_ARRAY | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79502e4a7a42a4c83957c0ef6b470fa9753db6fd
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317461"
---
# <a name="bstrarray"></a>BSTR_ARRAY
Struktura, która opisuje tablicę ciągów.

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

## <a name="terms"></a>Warunki
dwCount  
Liczba parametrów w `Members` tablicy.

Elementy członkowskie  
Tablica ciągów.

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracana z [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) metody.

[Tylko w języku C++] Każdy ciąg pojedynczych musi zostać uwolniona za pomocą `SysFreeString`i `Members` tablicy musi być zwolniona przez `CoTaskMemFree`.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)  
[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
