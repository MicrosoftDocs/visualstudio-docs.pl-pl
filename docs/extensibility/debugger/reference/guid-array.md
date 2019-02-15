---
title: GUID_ARRAY | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3aa33d8cef230d07c9b5f7cd3bd11a538fa651a
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315524"
---
# <a name="guidarray"></a>GUID_ARRAY
W tym artykule opisano tablicę unikatowych identyfikatorów dla silniki debugowania dostępnych.

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="terms"></a>Warunki
dwCount  
Liczba unikatowych identyfikatorów w tablicy.

Elementy członkowskie  
Tablica, która zawiera unikatowe identyfikatory.

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracany przez [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
