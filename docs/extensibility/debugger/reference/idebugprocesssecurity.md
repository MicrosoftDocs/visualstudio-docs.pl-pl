---
description: IDebugProcessSecurity jest implementowany przez dostawcę portu w celu ostrzeżenia użytkownika, który dołączany do procesu jest niebezpieczny.
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5e2ca72cc3d9c1d204c6fb1f90ccc9b03060cff
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166102"
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
