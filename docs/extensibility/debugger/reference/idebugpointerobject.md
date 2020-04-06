---
title: IDebugPointerObject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b28189b3f0a07a27f5e4478f64963a63d634db5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725490"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje obiekt wskaźnika.

## <a name="syntax"></a>Składnia

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Oceniający wyrażenie implementuje ten interfejs do reprezentowania obiektu wskaźnika.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Interfejs [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) można uzyskać ten interfejs przy `IDebugObject` użyciu [QueryInterface,](/cpp/atl/queryinterface) jeśli reprezentuje wskaźnik.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod dziedziczonych z [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) `IDebugPointerObject` interfejs udostępnia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Pobiera obiekt, do którego wskazuje interfejs.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Pobiera wartość, do której wskazuje interfejs jako seria kolejnych bajtów.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Ustawia wartość, do której wskazuje interfejs z serii kolejnych bajtów.|

## <a name="remarks"></a>Uwagi
 Oceniający wyrażenie używa tego interfejsu do reprezentowania wskaźnika w drzewie analizy.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
