---
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edfcb7d1603160c2f857508c3dd32ce0696b6d7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352992"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Reprezentuje dokument sumy kontrolnej dla żądania punktu przerwania.

## <a name="syntax"></a>Składnia

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Zaimplementowane przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pakiet debugowania i używane przez aparaty debugowania.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugBreakpointChecksumRequest2`.

|Metoda|Opis|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Pobiera suma kontrolna dokumentu żądania punktu przerwania podane Unikatowy identyfikator algorytmu sumy kontrolnej do użycia.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Określa, czy suma kontrolna jest włączone dla tego dokumentu.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll