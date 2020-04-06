---
title: IDebugMemoryContext2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727429"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Ten interfejs reprezentuje pozycję w przestrzeni adresowej komputera z systemem debugowania programu.

## <a name="syntax"></a>Składnia

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania adresu w pamięci.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) lub [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) zwraca ten interfejs. Ponadto wywołania [Dodaj](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) i [Odejmij](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) zwracają nowe kopie tego interfejsu po zastosowaniu odpowiedniej operacji arytmetycznej.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugMemoryContext2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Pobiera nazwę wyświetlania użytkownika dla tego kontekstu.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Pobiera informacje, które opisuje ten kontekst.|
|[Dodaj](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Dodaje określoną wartość do adresu bieżącego kontekstu, aby utworzyć nowy kontekst.|
|[Odejmij](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Odejmuje określoną wartość od adresu bieżącego kontekstu, aby utworzyć nowy kontekst.|
|[Porównanie](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Porównuje dwa konteksty w sposób wskazany przez porównać flagi.|

## <a name="remarks"></a>Uwagi
 Okno **pamięci** programu Visual Studio wywołuje [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) w celu uzyskania `IDebugMemoryContext2` interfejsu, który zawiera obliczone wyrażenie używane dla adresu pamięci. Ten kontekst jest następnie przekazywane do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) i [WriteAt,](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) aby określić adres do odczytu lub zapisu.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
