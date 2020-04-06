---
title: IDebugCodeContext3 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3f81168d9af7fbbb93b5c59f3ab19a17107b56b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734191"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Rozszerza interfejs [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) aby umożliwić pobieranie interfejsów modułu i procesu.

## <a name="syntax"></a>Składnia

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Zaimplementowane przez aparaty [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugowania i używane przez pakiet debugowania.

## <a name="methods"></a>Metody
 Oprócz metod w interfejsie, `IDebugCodeContext2` ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Pobiera odwołanie do interfejsu modułu debugowania.|
|[GetProcess ( GetProcess )](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Pobiera odwołanie do interfejsu procesu debugowania.|

## <a name="remarks"></a>Uwagi
 Jest to opcjonalny interfejs, który zazwyczaj nie musi być zaimplementowany.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
