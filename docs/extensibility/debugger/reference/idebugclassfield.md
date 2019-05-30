---
title: IDebugClassField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05d01ee3867481b8ab9bb100f2623c1197492666
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329465"
---
# <a name="idebugclassfield"></a>IDebugClassField
Ten interfejs reprezentuje klasę jako typu.

## <a name="syntax"></a>Składnia

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsu. Ten interfejs jest specjalizację, który reprezentuje typ klasy.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Liczba interfejsów mają metod zwracających takiego postępowania łącznie interfejs [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), i [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). Ponadto, możesz użyć [QueryInterface](/cpp/atl/queryinterface) uzyskać ten interfejs z [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsu, jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metoda zwraca flagę `FIELD_TYPE_CLASS`.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metod na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsów, ten interfejs wykonuje następujące czynności:

|Metoda|Opis|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Tworzy moduł wyliczający dla klasy bazowe tej klasy.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Określa, jeśli określony interfejs jest zdefiniowana w klasie.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Tworzy moduł wyliczający dla klas zagnieżdżonych tej klasy.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Pobiera klasę, która otacza tej klasy.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Tworzy moduł wyliczający interfejsy implementowane przez tę klasę.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Tworzy moduł wyliczający konstruktory tej klasy.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Pobiera nazwę indeksatora domyślne.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Tworzy moduł wyliczający dla zagnieżdżonych moduły wyliczające tej klasy.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)