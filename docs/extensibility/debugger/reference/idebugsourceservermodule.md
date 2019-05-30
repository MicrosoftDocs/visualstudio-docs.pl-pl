---
title: IDebugSourceServerModule | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5bb686ff492ca836d35b21d54298876314ecb8d5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321916"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Reprezentuje informacji o serwerze źródłowym, który jest zawarty w pliku PDB.

## <a name="syntax"></a>Składnia

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez debugera aparatów i wykorzystana przez debugera interfejsu użytkownika.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugSourceServerModule`.

|Metoda|Opis|
|------------|-----------------|
|[GetSourceServerData, metoda](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Pobiera tablicę informacji o serwerze źródłowym.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll