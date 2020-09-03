---
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ef4162469651e4b69502d3a9639d1e86c62e0b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718226"
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
