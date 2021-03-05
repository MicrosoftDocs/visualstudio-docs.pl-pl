---
description: Umożliwia aparatowi debugowania korzystającemu z modelu DCOM zaproszenie interfejsu użytkownika programu Visual Studio, aby upewnić się, że Zapora nie blokuje zdalnego debugowania.
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf8659a1bc4af55a9809a3c85548b971a7193b26
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166531"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Umożliwia aparatowi debugowania korzystającemu z modelu DCOM zaproszenie [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika, aby upewnić się, że Zapora nie blokuje zdalnego debugowania.

## <a name="syntax"></a>Składnia

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Zaimplementowane przez obiekt port Menedżera debugowania sesji.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugFirewallConfigurationCallback2` .

|Metoda|Opis|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Żąda, aby zapora nie blokowała zdalnego debugowania.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
