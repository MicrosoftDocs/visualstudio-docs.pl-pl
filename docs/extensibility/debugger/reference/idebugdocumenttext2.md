---
title: Tekst IDebugDocumentText2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b5def7f6cc4ac5ced91ca0a273ce750003dca20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731558"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Ten interfejs reprezentuje dokument tekstowy.

## <a name="syntax"></a>Składnia

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, gdy kod źródłowy, który musi dostarczyć, jest w formie tekstowej. Ponieważ jest to najbardziej typowy przypadek, jeśli DE implementuje interfejs [IDebugDocument2,](../../../extensibility/debugger/reference/idebugdocument2.md) należy również zaimplementować `IDebugDocumentText2` interfejs.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj `QueryInterface` tej metody, aby `IDebugDocument2` uzyskać ten interfejs z interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod w interfejsie, `IDebugDocument2` ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Pobiera rozmiar tekstu w tym miejscu w dokumencie.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Pobiera tekst z określonego stanowiska w dokumencie.|

## <a name="remarks"></a>Uwagi
 Obiekt, który implementuje ten interfejs <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> musi również implementować interfejs, który dostarcza <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejs dla obiektu [IDebugDocumentTextEvents2.](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
