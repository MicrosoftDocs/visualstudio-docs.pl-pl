---
description: Przedstawia sumę kontrolną dokumentu dla żądania punktu przerwania.
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 78361429e371bf19ee1fea27c090af80c2b79b73
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078087"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Przedstawia sumę kontrolną dokumentu dla żądania punktu przerwania.

## <a name="syntax"></a>Składnia

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Zaimplementowane przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pakiet debugowania i używane przez aparaty debugowania.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugBreakpointChecksumRequest2` .

|Metoda|Opis|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Pobiera sumę kontrolną dokumentu dla żądania punktu przerwania, który ma unikatowy identyfikator algorytmu sumy kontrolnej do użycia.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Określa, czy suma kontrolna jest włączona dla tego dokumentu.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
