---
title: IDebugDocumentPosition2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63742f220d5a776fca180a3f9f7fe9c15e04c66a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731638"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Ten interfejs reprezentuje abstrakcyjną pozycję w pliku źródłowym.

## <a name="syntax"></a>Składnia

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Visual Studio zazwyczaj implementuje ten interfejs. Aparat debugowania (DE) również implementuje ten interfejs, jeśli musi dostarczyć własny kod źródłowy (jak wtedy, gdy DE implementuje interfejs [IDebugDocument2).](../../../extensibility/debugger/reference/idebugdocument2.md)

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest przekazywany jako argument do [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Jest również dostarczany jako część unii [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (w szczególności [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) struktury), która jest z kolei częścią [struktury BP_REQUEST_INFO,](../../../extensibility/debugger/reference/bp-request-info.md) która jest używana do tworzenia oczekującego punktu przerwania.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugDocumentPosition2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Pobiera nazwę pliku źródłowego, który zawiera tę pozycję dokumentu.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Pobiera dokument zawierający.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Określa, czy to stanowisko znajduje się w danym dokumencie.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Pobiera zakres dla tej pozycji dokumentu.|

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
