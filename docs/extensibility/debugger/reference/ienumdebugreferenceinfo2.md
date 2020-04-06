---
title: IEnumDebugReferenceInfo2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6132235a7e4789c7d9efe5bae9d7fd531112dab4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715268"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Ten interfejs wylicza [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur.

## <a name="syntax"></a>Składnia

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs jako część jego obsługi odwołań do obiektów w pamięci. Ten interfejs musi być zaimplementowany tylko wtedy, gdy odwołania są obsługiwane.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Visual Studio wywołuje [EnumChildren,](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IEnumDebugReferenceInfo2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Pobiera określoną liczbę [struktur DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) w sekwencji wyliczenia.|
|[Pominąć](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Pomija określoną liczbę [struktur DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) w sekwencji wyliczenia.|
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Resetuje sekwencję wyliczenia do początku.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Tworzy wyliczenia, który zawiera ten sam stan wyliczenia jako bieżącego wylicznika.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Pobiera liczbę [struktur DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) w wyliczacza.|

## <a name="remarks"></a>Uwagi
 Odwołanie jest zasadniczo typu i adresu, podczas gdy właściwość jest nazwa, typ i adres. Odwołanie będzie się powtarzać tak długo, jak obiekt, o którym mowa istnieje w pamięci. Zobacz [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) aby uzyskać więcej informacji.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
