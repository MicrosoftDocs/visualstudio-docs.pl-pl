---
title: IDebugDocumentContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d31a78412a1a6b20518b6f38ba76b7964cbdbe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731734"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Ten interfejs reprezentuje pozycję w dokumencie pliku źródłowego.

## <a name="syntax"></a>Składnia

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs w ramach obsługi debugowania na poziomie kodu źródłowego. Oprócz pozycji w kodzie źródłowym, ten interfejs dostarcza metody do porównywania kontekstów i nawigowania w dokumencie kodu źródłowego.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Metody na kilku interfejsach — zwykle interfejsy [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) i [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) zwracają ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugDocumentContext2` .

|Metoda|Opis|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Pobiera dokument zawierający kontekst tego dokumentu.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Pobiera nazwę dokumentu, który zawiera ten kontekst dokumentu.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Pobiera listę wszystkich kontekstów kodu skojarzonych z tym kontekstem dokumentu.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Pobiera język skojarzony z tym kontekstem dokumentu.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Pobiera zakres instrukcji pliku tego kontekstu dokumentu.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Pobiera zakres źródła plików tego kontekstu dokumentu.|
|[Porównaj](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Porównuje ten kontekst dokumentu z daną tablicą kontekstów dokumentów.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Przenosi kontekst dokumentu o określoną liczbę instrukcji lub wierszy.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
