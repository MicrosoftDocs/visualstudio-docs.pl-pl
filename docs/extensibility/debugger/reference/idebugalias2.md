---
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abd220cd8c67318981fda79d3be8a0014ab61de1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321727"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Reprezentuje liczbowych alias dla zmiennej i umożliwia ewaluatora wyrażeń (EE), można uzyskać domeny aplikacji aliasu.

## <a name="syntax"></a>Składnia

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez aparat debugowania zarządzanego (DE).

## <a name="methods"></a>Metody
 Oprócz metod na [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfejsu, ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Pobiera identyfikator domeny aplikacji.|

## <a name="remarks"></a>Uwagi
 Alias jest liczbą dziesiętną w postaci ciągu, a następnie znak #, na przykład 1001#.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll