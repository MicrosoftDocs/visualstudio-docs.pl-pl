---
title: IDebugPointerField | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a69797cc513b96c364f0357f22788fc9bcd65657
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725593"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Ten interfejs reprezentuje typ wskaźnika.

## <a name="syntax"></a>Składnia

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symbolu implementuje ten interfejs do reprezentowania wskaźnika.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać ten interfejs z interfejsu [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca `FIELD_TYPE_POINTER`.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod na `IDebugField` i `IDebugContainerField` interfejsy, ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Zwraca [pole IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisujące obiekt docelowy wskaźnika.|

## <a name="remarks"></a>Uwagi
 W języku C/C++ wskaźnik może być kontenerem, jeśli jest używany z notacją tablicy. Na przykład, `char *pString` `pString` biorąc pod uwagę `char`, ma typ wskaźnika do . `pString[3]`ma typ kontenera, który jest `char` wskaźnikiem do który odwołuje się do czwartego elementu tego kontenera.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
