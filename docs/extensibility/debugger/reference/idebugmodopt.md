---
title: IDebugModOpt | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e142ed1229f59cfc22ff33cba48e9e35eb4e4406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726969"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Reprezentuje modyfikator opcjonalny debugowania.

## <a name="syntax"></a>Składnia

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Uzyskane z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu, który reprezentuje klasę lub metodę.

## <a name="methods"></a>Metody
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Pobiera listę modyfikatorów opcjonalnych.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
