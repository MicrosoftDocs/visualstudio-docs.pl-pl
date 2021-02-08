---
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8dfc4b3defc0b74c1e22c45670209682692a4807
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837700"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Reprezentuje informacje o serwerze źródłowym, które znajdują się w pliku PDB.

## <a name="syntax"></a>Składnia

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez aparaty debugera i zużywany przez interfejs użytkownika debugera.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugSourceServerModule` .

|Metoda|Opis|
|------------|-----------------|
|[GetSourceServerData, metoda](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Pobiera tablicę informacji o serwerze źródłowym.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
