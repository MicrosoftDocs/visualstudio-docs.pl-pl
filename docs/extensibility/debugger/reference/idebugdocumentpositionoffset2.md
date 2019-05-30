---
title: IDebugDocumentPositionOffset2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3793d54249fca1dc867cfe4072326245a67852cb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333270"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Reprezentuje pozycji w pliku źródłowym jako przesunięcie znaku.

## <a name="syntax"></a>Składnia

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Implementowany przez środowisko IDE, są używane przez aparaty debugowania.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugDocumentPositionOffset2`.

|Metoda|Opis|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Pobiera zakres dla bieżącej pozycji dokumentu.|

## <a name="remarks"></a>Uwagi
 Spowoduje to zwrócenie te same informacje co [getrange —](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ale w `char` powoduje przesunięcie od początku dokumentu. Przedstawia dokumentu, takie jak jego istniałby na dysku, oznacza to Jednowymiarowa tablica znaków, a nie informacji wierszy i kolumn, który zazwyczaj jest zwracany.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)