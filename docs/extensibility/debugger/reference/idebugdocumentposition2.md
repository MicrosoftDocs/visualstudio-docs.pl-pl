---
title: IDebugDocumentPosition2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c2fbce0154a5ebefd04ea3614d16db16799510
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333423"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Ten interfejs stanowi abstrakcyjną pozycji w pliku źródłowym.

## <a name="syntax"></a>Składnia

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Visual Studio zazwyczaj implementują ten interfejs. Aparat debugowania (DE) będzie także implementować ten interfejs, jeśli konieczne jest podanie własnego kodu źródłowego (jako po implementuje DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfejsu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest przekazywany jako argument do [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Również jest dostarczany jako część [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Unii (w szczególności [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) struktury) który z kolei jest częścią [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktury który jest używany podczas tworzenia oczekujący punkt przerwania.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugDocumentPosition2`.

|Metoda|Opis|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Pobiera nazwę pliku pliku źródłowego, który zawiera położenie tego dokumentu.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Pobiera dokumentu zawierającego.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Określa, jeśli ta pozycja jest zawarty w danym dokumencie.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Pobiera zakres dla tej pozycji dokumentu.|

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)