---
title: IDebugField | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728753"
---
# <a name="idebugfield"></a>IDebugField
Ten interfejs reprezentuje pole, czyli opis symbolu lub typu.

## <a name="syntax"></a>Składnia

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symbolu implementuje ten interfejs jako klasę podstawową dla wszystkich pól.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest klasą podstawową dla wszystkich pól. Na podstawie wartości zwracanej [GetKind,](../../../extensibility/debugger/reference/idebugfield-getkind.md)ten interfejs może zwracać bardziej wyspecjalizowane interfejsy przy użyciu [QueryInterface](/cpp/atl/queryinterface). Ponadto wiele interfejsów `IDebugField` zwraca obiekty z różnych metod.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugField`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Pobiera wyświetlane informacje o symbolu lub typie.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Pobiera rodzaj pola.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Pobiera typ pola.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Pobiera kontener pola.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Pobiera adres pola.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Pobiera rozmiar pola w bajtach.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Pobiera rozszerzone informacje o polu.|
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Porównuje dwa pola.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Pobiera niezależne od typu informacje o symbolu lub typie.|

## <a name="remarks"></a>Uwagi
 Typ jest odpowiednikiem języka `typedef`C .

 W poniższym przykładzie języka `weather` C++ jest `sunny` `stormy` typem klasy i są symbolami:

```cpp
class weather;
weather sunny;
weather stormy;
```

 O tym, czy pole reprezentuje symbol czy typ, można określić, wywołując [program GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) i sprawdzając [wynik FIELD_KIND.](../../../extensibility/debugger/reference/field-kind.md) Jeśli `FIELD_KIND_TYPE` bit jest ustawiony, pole jest typem, a jeśli `FIELD_KIND_SYMBOL` bit jest ustawiony, jest symbolem.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
