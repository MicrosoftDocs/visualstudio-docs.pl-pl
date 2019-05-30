---
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09b4c04b996d180f1975ee1e9ad3a9a95cd1b76a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337451"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Umożliwia to aparat debugowania, który używa modelu DCOM poprosić [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika, aby upewnić się, że Zapora nie blokuje debugowanie zdalne.

## <a name="syntax"></a>Składnia

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Implementowany przez obiekt portów Menedżer debugowania sesji.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugFirewallConfigurationCallback2`.

|Metoda|Opis|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Żądania, że Zapora nie blokuje debugowanie zdalne.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll