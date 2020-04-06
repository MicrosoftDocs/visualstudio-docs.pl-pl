---
title: IDebugSourceServerModule | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2c362bc4a103c707238acfa3b3148f00c0e25be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719914"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Reprezentuje informacje o serwerze źródłowym zawarte w pliku PDB.

## <a name="syntax"></a>Składnia

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez aparaty debugera i używane przez interfejs użytkownika debugera.

## <a name="methods"></a>Metody
 W poniższej tabeli `IDebugSourceServerModule`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetSourceServerData, metoda](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Pobiera tablicę informacji o serwerze źródłowym.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
