---
description: Rozszerza interfejs IDebugCodeContext2, aby umożliwić pobieranie interfejsów modułu i procesów.
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db806a4b45e855533e4ded1419f2d2117fb4f912
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164022"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Rozszerza interfejs [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , aby umożliwić pobieranie interfejsów modułu i procesów.

## <a name="syntax"></a>Składnia

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Zaimplementowane przez aparaty debugowania i używane przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pakiet debugowania.

## <a name="methods"></a>Metody
 Oprócz metod w `IDebugCodeContext2` interfejsie, ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Pobiera odwołanie do interfejsu modułu debugowania.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Pobiera odwołanie do interfejsu procesu debugowania.|

## <a name="remarks"></a>Uwagi
 Jest to opcjonalny interfejs, który zwykle nie musi być zaimplementowany.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
