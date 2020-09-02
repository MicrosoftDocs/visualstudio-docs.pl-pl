---
title: IEnumDebugObjects | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716262"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje kolekcję obiektów implementujących interfejs [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .

## <a name="syntax"></a>Składnia

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs, aby zapewnić zestawy obiektów implementujących interfejs [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) . Należy zauważyć, że nie jest to standardowe wyliczenie COM z powodu obecności metody [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Ten interfejs implementuje następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Pobiera następny zestaw obiektów [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) z wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Pomija określoną liczbę wpisów.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Resetuje Wyliczenie do pierwszego wpisu.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Pobiera kopię bieżącego wyliczania.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs umożliwia aparatowi debugowania Wyliczenie na zestawie obiektów w tablicy.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
