---
description: Reprezentuje opcjonalny modyfikator debugowania.
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffb235d58c254d130636da0f4b97961c11f9a372
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087902"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Reprezentuje opcjonalny modyfikator debugowania.

## <a name="syntax"></a>Składnia

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Uzyskany z obiektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , który reprezentuje klasę lub metodę.

## <a name="methods"></a>Metody
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Pobiera listę opcjonalnych modyfikatorów.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
