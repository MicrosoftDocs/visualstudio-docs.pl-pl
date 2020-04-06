---
title: IDebugDocumentContext2 | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731734"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Ten interfejs reprezentuje pozycję w dokumencie pliku źródłowego.

## <a name="syntax"></a>Składnia

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs jako część jego obsługi debugowania na poziomie kodu źródłowego. Oprócz pozycji w kodzie źródłowym ten interfejs dostarcza metody porównywania kontekstów i nawigowania po dokumencie kodu źródłowego.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Metody na kilku interfejsach, najczęściej [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) i [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) interfejsów, zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugDocumentContext2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Pobiera dokument, który zawiera ten kontekst dokumentu.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Pobiera wyświetlaną nazwę dokumentu, który zawiera ten kontekst dokumentu.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Pobiera listę wszystkich kontekstów kodu skojarzonych z tym kontekstem dokumentu.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Pobiera język skojarzony z tym kontekstem dokumentu.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Pobiera zakres instrukcji pliku tego kontekstu dokumentu.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Pobiera zakres źródła plików tego kontekstu dokumentu.|
|[Porównanie](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Porównuje ten kontekst dokumentu z daną tablicą kontekstów dokumentu.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Przenosi kontekst dokumentu o daną liczbę instrukcji lub wierszy.|

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
