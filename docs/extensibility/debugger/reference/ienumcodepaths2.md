---
title: Ścieżka IEnumCodePaths2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89c8cac9a7c2baa020002fe852330639d7081982
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717720"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Ten interfejs reprezentuje listę ścieżek kodu.

## <a name="syntax"></a>Składnia

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania listy ścieżek kodu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [EnumCodePaths,](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IEnumCodePaths2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Pobiera określoną liczbę ścieżek kodu w sekwencji wyliczenia.|
|[Pominąć](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Pomija określoną liczbę ścieżek kodu w sekwencji wyliczenia.|
|[Resetuj](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Resetuje sekwencję wyliczenia do początku.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Tworzy wyliczenia, który zawiera ten sam stan wyliczenia jako bieżącego wylicznika.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Pobiera liczbę ścieżek kodu w wyliczacza.|

## <a name="remarks"></a>Uwagi
 Ścieżka kodu reprezentuje punkt gałęzi lub wywołanie funkcji w programie. Lista ścieżek kodu reprezentuje ścieżkę, za pośrednictwem której wykonane jest wykonanie kodu.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
