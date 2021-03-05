---
description: Umożliwia wykonywanie zapytań dotyczących informacji o komputerze docelowym.
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a9c7e940c2284b5b39097226f9a5b0c3b34a0d18
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222955"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Umożliwia wykonywanie zapytań dotyczących informacji o komputerze docelowym.

## <a name="syntax"></a>Składnia

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez obiekty portów Menedżera debugowania sesji.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugWindowsComputerPort2` .

|Metoda|Opis|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Pobiera informacje o komputerze, na którym działa debuger.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
