---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af72993a4a02ce7d25858bf3bd4f0690e0d30f5a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923101"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Ten interfejs reprezentuje dokument tekstowy.

## <a name="syntax"></a>Składnia

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, gdy kod źródłowy wymagany do dostarczenia jest w postaci tekstowej. Ponieważ jest to najbardziej typowy przypadek, Jeśli DE implementuje interfejs [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , powinien również zaimplementować `IDebugDocumentText2` interfejs.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj `QueryInterface` metody, aby uzyskać ten interfejs z `IDebugDocument2` interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod w `IDebugDocument2` interfejsie, ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetSize —](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Pobiera rozmiar tekstu w tym miejscu dokumentu.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Pobiera tekst z określonej pozycji w dokumencie.|

## <a name="remarks"></a>Uwagi
 Obiekt, który implementuje ten interfejs, również musi implementować <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfejs, który dostarcza <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejs dla obiektu [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
