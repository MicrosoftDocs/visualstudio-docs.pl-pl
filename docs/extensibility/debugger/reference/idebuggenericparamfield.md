---
description: Reprezentuje parametr dla ogólnego typu kodu zarządzanego.
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2dc01aaf3485e89ac32b4a4fd86c7491a1f96853
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091932"
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
