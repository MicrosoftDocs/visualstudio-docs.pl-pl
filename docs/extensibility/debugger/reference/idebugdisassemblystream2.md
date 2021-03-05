---
description: Ten interfejs reprezentuje strumień instrukcji.
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 760d77ced3cc07da2dd02c21cf3ed0200df14231
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166570"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Ten interfejs reprezentuje strumień instrukcji.

## <a name="syntax"></a>Składnia

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania implementuje ten interfejs, aby obsługiwał rozzbiór kodu programu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie metody [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugDisassemblyStream2` .

|Metoda|Opis|
|------------|-----------------|
|[Przeczytaj](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Odczytuje instrukcje zaczynające się od bieżącej pozycji w strumieniu demontażu.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Przenosi wskaźnik odczytu w strumieniu demontażu przez daną liczbę instrukcji względem określonego położenia.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Zwraca identyfikator lokalizacji kodu dla określonego kontekstu kodu.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Zwraca obiekt kontekstu kodu odpowiadający określonemu identyfikatorowi lokalizacji kodu.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Zwraca identyfikator lokalizacji kodu, który reprezentuje bieżącą lokalizację kodu.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Pobiera dokument źródłowy skojarzony z tym strumieniem odzestawu.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Pobiera zakres tego strumienia rozasemblera.|
|[GetSize —](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Pobiera rozmiar tego strumienia rozbudowania.|

## <a name="remarks"></a>Uwagi
 Strumień demontażu można utworzyć w taki sposób, aby reprezentować całą przestrzeń adresową lub tylko funkcję lub moduł w miejscu. Każda instrukcja jest reprezentowana przez strukturę [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) zwracaną przez wywołanie metody [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
