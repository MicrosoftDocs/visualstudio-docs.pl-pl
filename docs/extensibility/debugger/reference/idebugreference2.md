---
title: IDebugReference2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52f655afd35ed316080a3a85ccfae047aa50d87f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720261"
---
# <a name="idebugreference2"></a>IDebugReference2
Ten interfejs reprezentuje odwołanie do właściwości ramki stosu lub innej właściwości.

> [!NOTE]
> `IDebugReference2`jest zarezerwowany do wykorzystania w przyszłości, `E_NOTIMPL`a wszystkie jego metody powinny powrócić .

## <a name="syntax"></a>Składnia

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs do reprezentowania odwołania do określonego rodzaju wartości. Na przykład wartość może być wartością liczbową w wyniku oceny wyrażenia, kontekstu pamięci używanego do wyświetlania pamięci lub listy rejestrów i ich wartości.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [GetReference,](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) aby uzyskać ten interfejs. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) i [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) również zwrócić ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugReference2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Pobiera [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury, która opisuje to odwołanie.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Ustawia wartość tego odwołania z ciągu.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Ustawia wartość tego odwołania z innego odwołania.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Wylicza wiązki podrzędne tego odwołania.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Pobiera element nadrzędny tego odwołania.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Pobiera najbardziej pochodne odwołanie tego odwołania.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Pobiera bajtów pamięci, do których odwołuje się to odwołanie.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Pobiera kontekst pamięci dla tego odwołania.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Pobiera rozmiar, w bajtach, tego odwołania.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Ustawia ten typ odwołania.|
|[Porównanie](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Porównuje to odwołanie z innym.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
> To użycie "właściwość" nie należy mylić z tym znaczenie `IDebugReference2` zmiennej członkowskiej klasy, chociaż może reprezentować taką jednostkę.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) reprezentuje właściwość, podczas gdy `IDebugReference2` reprezentuje odwołanie do właściwości, zazwyczaj odwołanie do obiektu w programie debugowane.

 Główną różnicą między właściwością a odwołaniem jest to, że właściwość odwołuje się do nazwanego wystąpienia obiektu, podczas gdy odwołanie odwołuje się do wystąpienia bez nazwy. Na przykład właściwość może odwoływać się do obiektu `"a.b"`w stercie programu przez . Inna właściwość może odnosić `"c.d"`się do tego samego obiektu co . Sposób odwoływania się do tej `"a.b"` `"c.d"` właściwości wymaga, aby lub być w zakresie. Odwołanie do tego samego obiektu jest bezimienny; obiekt może być określany tak długo, jak pamięć dla tego obiektu jest prawidłowa.

 Interfejs `IDebugProperty2` można traktować jako wartość z nazwą, typem i adresem. Z `IDebugReference2`drugiej strony, można go traktować jako rodzaj i adres.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
