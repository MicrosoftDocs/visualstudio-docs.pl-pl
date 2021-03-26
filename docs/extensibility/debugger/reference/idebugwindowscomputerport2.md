---
description: Umożliwia wykonywanie zapytań dotyczących informacji o komputerze docelowym.
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fd2d499fad2e05a8f295e2c087289fcb9477f90f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083482"
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
