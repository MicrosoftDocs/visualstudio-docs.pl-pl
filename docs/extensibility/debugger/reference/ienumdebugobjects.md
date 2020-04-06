---
title: IEnumDebugObjects | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c04409fb695613fea5d54b285946c04719fbe5b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716262"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje kolekcję obiektów implementujących interfejs [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)

## <a name="syntax"></a>Składnia

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Oceniający wyrażenie implementuje ten interfejs, aby zapewnić zestawy obiektów, które implementują interfejs [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md) Należy zauważyć, że nie jest to standardowe wyliczenie COM ze względu na obecność [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) metody.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Ten interfejs implementuje następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Pobiera następny zestaw obiektów [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) z wyliczenia.|
|[Pominąć](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Pomija określoną liczbę wpisów.|
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Resetuje wyliczenie do pierwszego wpisu.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Pobiera kopię bieżącego wyliczenia.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs umożliwia aparat debugowania do wyliczenia przez zestaw obiektów w tablicy.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
