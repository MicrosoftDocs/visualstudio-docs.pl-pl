---
title: IDebugDocumentContext2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe54a6d3e97fc40f915c42c4aa5397165416b073
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326644"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Ten interfejs reprezentuje pozycji w dokumencie pliku źródłowym.

## <a name="syntax"></a>Składnia

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs jako część obsługę debugowania poziomu kodu źródłowego. Oprócz pozycji w kodzie źródłowym ten interfejs dostarcza metody do porównywania kontekstów ani nawigować przez dokumentu kodu źródłowego.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Metody na kilka interfejsów najczęściej [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) i [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) interfejsów, zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugDocumentContext2`.

|Metoda|Opis|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Pobiera dokument, który zawiera ten kontekst dokumentu.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Pobiera nazwę zawiera dokument, który zawiera ten kontekst dokumentu.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Pobiera listę wszystkich kontekstach kodu skojarzone z tym kontekstem dokumentu.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Pobiera język skojarzone z tym kontekstem dokumentu.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Pobiera zakres instrukcji pliku tego kontekstu dokumentu.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Pobiera zakres źródłowy plik tego kontekstu dokumentu.|
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Porównuje ten kontekst dokumentu do danej tablicy kontekstów dokumentu.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Przenosi kontekstu dokumentu o podanej liczbie wierszy lub instrukcji.|

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)