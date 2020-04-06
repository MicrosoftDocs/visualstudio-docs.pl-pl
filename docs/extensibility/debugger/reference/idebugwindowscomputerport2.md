---
title: IDebugWindowsComputerPort2 | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718226"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Umożliwia wykonywanie zapytań o informacje o komputerze docelowym.

## <a name="syntax"></a>Składnia

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez obiekty portów menedżera debugowania sesji.

## <a name="methods"></a>Metody
 W poniższej tabeli `IDebugWindowsComputerPort2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Pobiera informacje o komputerze, na którym jest uruchomiony debuger.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
