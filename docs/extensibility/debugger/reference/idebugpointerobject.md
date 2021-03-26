---
description: Ten interfejs reprezentuje obiekt wskaźnika.
title: IDebugPointerObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af6b8f6022a9363eb5391d6f0519603fa48668c2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087603"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje obiekt wskaźnika.

## <a name="syntax"></a>Składnia

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs, aby reprezentować obiekt wskaźnika.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Interfejs [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) może uzyskać ten interfejs za pomocą [polecenia QueryInterface](/cpp/atl/queryinterface) , jeśli `IDebugObject` reprezentuje wskaźnik.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod dziedziczonych z [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugPointerObject` interfejs uwidacznia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Pobiera obiekt, do którego wskazuje interfejs.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Pobiera wartość, do której interfejs wskazuje serię kolejnych bajtów.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Ustawia wartość, do której interfejs wskazuje z serii kolejnych bajtów.|

## <a name="remarks"></a>Uwagi
 Ewaluatora wyrażeń używa tego interfejsu do reprezentowania wskaźnika w drzewie analizy.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
