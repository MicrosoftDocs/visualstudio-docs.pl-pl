---
description: IDebugProcessSecurity jest implementowany przez dostawcę portu w celu ostrzeżenia użytkownika, który dołączany do procesu jest niebezpieczny.
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7466d88be9460a2b4680fc7d14a741df9238ea0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076267"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` Program jest implementowany przez dostawcę portu w celu ostrzeżenia użytkownika, który dołączany do procesu jest niebezpieczny.

## <a name="syntax"></a>Składnia

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugProcessSecurity` .

|Metoda|Opis|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Pobiera nazwę użytkownika z dostawcy portów.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Ostrzega użytkownika, który dołączany do procesu debugowania jest niebezpieczny.|

## <a name="remarks"></a>Uwagi
 Zaimplementuj ten interfejs, aby wyświetlić ostrzeżenie i zezwolić użytkownikowi na anulowanie, jeśli proces, do którego chcesz dołączyć, może być traktowany jako niebezpieczny.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Porty](../../../extensibility/debugger/ports.md)
- [Dostawcy portów](../../../extensibility/debugger/port-suppliers.md)
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
