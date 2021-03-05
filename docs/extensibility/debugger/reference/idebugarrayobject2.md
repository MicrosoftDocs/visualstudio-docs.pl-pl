---
description: Reprezentuje zarządzany obiekt Array i pozwala ewaluatora wyrażeń (EE) określić indeks podstawowy (dolne granice) dla tablicy.
title: IDebugArrayObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e6bb73834f53e22df63682663539b5f01685b30
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102174127"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Reprezentuje zarządzany obiekt Array i pozwala ewaluatora wyrażeń (EE) określić indeks podstawowy (dolne granice) dla tablicy.

## <a name="syntax"></a>Składnia

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Jest to implementowane przez zarządzany aparat debugowania (DE).

## <a name="methods"></a>Metody
 Oprócz metod interfejsu [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) , ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Pobiera indeksy podstawowe (dolne granice) dla każdego indeksu z określoną liczbą wymiarów w tablicy.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Określa, czy tablica ma zdefiniowane indeksy podstawowe (dolne granice).|

## <a name="remarks"></a>Uwagi
 Ewaluatora wyrażeń używa tego interfejsu do reprezentowania zarządzanych tablic w drzewie analizy.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
