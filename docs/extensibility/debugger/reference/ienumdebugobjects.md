---
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 749b3faf938fbc862fdf9b406127c898ee6b6d98
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727562"
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
|[Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Pobiera następny zestaw obiektów [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) z wyliczenia.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Pomija określoną liczbę wpisów.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Resetuje Wyliczenie do pierwszego wpisu.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Pobiera kopię bieżącego wyliczania.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs umożliwia aparatowi debugowania Wyliczenie na zestawie obiektów w tablicy.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft. VisualStudio. Debugger. Interop. dll

## <a name="see-also"></a>Zobacz także
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)