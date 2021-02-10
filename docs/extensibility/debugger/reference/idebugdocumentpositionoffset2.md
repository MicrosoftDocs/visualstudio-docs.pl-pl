---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69fbdef70fc9c95ef571ce0ce796199292417ca0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933560"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Reprezentuje pozycję w pliku źródłowym jako przesunięcie znaku.

## <a name="syntax"></a>Składnia

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Zaimplementowane przez środowisko IDE i używane przez aparaty debugowania.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugDocumentPositionOffset2` .

|Metoda|Opis|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Pobiera zakres dla bieżącego położenia dokumentu.|

## <a name="remarks"></a>Uwagi
 Ta funkcja zwraca te same informacje jak [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) , ale w `char` przesunięciach od początku dokumentu. Przedstawia to dokument, taki jak na dysku, czyli tablicę jednowymiarową znaków, zamiast informacji o wierszu i kolumnie, które są zwykle zwracane.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
