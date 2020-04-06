---
title: IDebugArrayObject2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8a6580d0cbdead7866bbc6dd106a2aa0ea56f76
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736225"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Reprezentuje obiekt tablicy zarządzanej i umożliwia oceniającemu wyrażenie (EE) określenie indeksu podstawowego (dolne granice) dla tablicy.

## <a name="syntax"></a>Składnia

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Jest to implementowane przez aparat debugowania zarządzanego (DE).

## <a name="methods"></a>Metody
 Oprócz metod na interfejsie [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Pobiera indeksy podstawowe (dolne granice) dla każdego indeksu, biorąc pod uwagę liczbę wymiarów w tablicy.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Określa, czy tablica ma zdefiniowane indeksy podstawowe (dolne granice).|

## <a name="remarks"></a>Uwagi
 Oceniający wyrażenie używa tego interfejsu do reprezentowania tablic zarządzanych w drzewie analizy.

## <a name="requirements"></a>Wymagania
 Nagłówek: Ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
