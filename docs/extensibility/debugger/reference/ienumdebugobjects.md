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
ms.openlocfilehash: dea4b4781fd8026c29436bbd37a6bfa6824e73b3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339483"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje kolekcję obiektów Implementowanie [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu.

## <a name="syntax"></a>Składnia

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluator wyrażeń implementuje ten interfejs w celu zapewnienia zestawów obiektów, które implementują [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu. Pamiętaj, że nie jest standardowy wyliczanie modelu COM z powodu obecności [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) metody.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
- [Metody GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Ten interfejs implementuje są następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Pobiera następny zestaw [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektów z wyliczenia.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Pomija określoną liczbę pozycji.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Resetuje wyliczenia do pierwszej pozycji.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Pobiera kopię bieżącego wyliczenia.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs umożliwia aparat debugowania, można wyliczyć zestawu obiektów w tablicy.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)