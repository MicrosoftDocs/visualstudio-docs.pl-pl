---
title: IDebugClassField | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b0e4cd7c851e65edf299f45ec97273804c25d8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734290"
---
# <a name="idebugclassfield"></a>IDebugClassField
Ten interfejs reprezentuje klasę jako typ.

## <a name="syntax"></a>Składnia

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symbolu implementuje ten interfejs na tym samym obiekcie, który implementuje interfejs [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Ten interfejs jest specjalizacji, która reprezentuje typ klasy.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wiele interfejsów ma metody, które mogą zwracać ten interfejs, w tym [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)i [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). Ponadto można użyć [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać ten interfejs z interfejsu [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) jeśli metoda [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca flagę `FIELD_TYPE_CLASS`.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod na [interfejsach IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) ten interfejs implementuje następujące czynności:

|Metoda|Opis|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Tworzy wyliczenia dla klas podstawowych tej klasy.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Określa, czy określony interfejs jest zdefiniowany w klasie.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Tworzy wyliczenia dla zagnieżdżonych klas tej klasy.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Pobiera klasę, która otacza tę klasę.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Tworzy moduł wyliczający dla interfejsów zaimplementowanych przez tę klasę.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Tworzy wyliczenia dla konstruktorów tej klasy.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Pobiera nazwę domyślnego indeksatora.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Tworzy wyliczenia dla zagnieżdżonych wyliczników tej klasy.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
