---
title: IDebugCodeContext2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 778602cc29049d855c418fd8fa416feb1ad8e9fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734209"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Ten interfejs reprezentuje pozycję początkową instrukcji kodu. Dla większości architektur w czasie wykonywania dzisiaj kontekst kodu można traktować jako adres w strumieniu wykonywania programu.

## <a name="syntax"></a>Składnia

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania implementuje ten interfejs, aby powiązać położenie instrukcji kodu do pozycji dokumentu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Metody na wielu interfejsach zwracają ten interfejs, najczęściej [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Jest również szeroko stosowany z [interfejsem IDebugDisassemblyStream2,](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) a także w informacjach o rozdzielczości punktu przerwania.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod na interfejsie [IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Pobiera kontekst dokumentu, który odpowiada kontekstu aktywnego kodu.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Pobiera informacje o języku dla tego kontekstu kodu.|

## <a name="remarks"></a>Uwagi
 Kluczową różnicą `IDebugCodeContext2` między interfejsem a [interfejsem IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) jest to, że `IDebugCodeContext2` jest zawsze wyrównany do instrukcji. Oznacza to, `IDebugCodeContext2` że an jest zawsze wskazuje na początku `IDebugMemoryContext2` instrukcji, natomiast może wskazywać na dowolny bajt pamięci w architekturze czasu wykonywania. `IDebugCodeContext2`jest zwiększany przez instrukcje, a nie przez podstawowy rozmiar magazynu (zazwyczaj bajt).

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
