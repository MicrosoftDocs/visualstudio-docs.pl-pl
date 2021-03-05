---
description: Reprezentuje parametr dla ogólnego typu kodu zarządzanego.
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c4ab1cd79826e2f9f07a4f325d701be4e9eb9c9d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172574"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Reprezentuje parametr dla ogólnego typu kodu zarządzanego.

## <a name="syntax"></a>Składnia

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Używane do obsługi typów ogólnych.

## <a name="methods"></a>Metody
 Oprócz metod interfejsu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Zwraca liczbę ograniczeń, które są skojarzone z tym parametrem ogólnym.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Pobiera ograniczenia, które są skojarzone z tym parametrem ogólnym.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Pobiera flagi dla tego parametru generycznego.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Pobiera indeks tego parametru generycznego.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Pobiera nazwę tego parametru generycznego.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Pobiera typ lub właściciela metody tego parametru generycznego.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
