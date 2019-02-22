---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6069b7c77995a855bfa47d1d369203f386b0302c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686876"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Ten interfejs reprezentuje dokument tekstowy.

## <a name="syntax"></a>Składnia

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, po kodzie źródłowym, trzeba go dostarczyć w postaci tekstu. Ponieważ jest to najbardziej typowy przypadek, gdy implementuje DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfejsu, powinien także implementować `IDebugDocumentText2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj `QueryInterface` metody uzyskania tego interfejsu z `IDebugDocument2` interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metod na `IDebugDocument2` interfejsu, ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Pobiera rozmiar tekstu, w tym miejscu w dokumencie.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Pobiera tekst z określonej pozycji w dokumencie.|

## <a name="remarks"></a>Uwagi
 Obiekt, który implementuje ten interfejs musi implementować też <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfejsu, które dostarcza <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejs na potrzeby [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) obiektu.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)