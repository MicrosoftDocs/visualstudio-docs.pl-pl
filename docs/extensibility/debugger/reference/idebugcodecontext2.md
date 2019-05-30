---
title: IDebugCodeContext2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59573736ca3cd0768d3383e5621d96dffdea9746
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338897"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Ten interfejs reprezentuje pozycję początkową instrukcji kodu. Dla większości architektury w czasie wykonywania, kontekst kodu można traktować jako adres w usłudze stream wykonywania programu.

## <a name="syntax"></a>Składnia

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania implementuje ten interfejs, aby powiązać pozycja instrukcję kodu położenie dokumentu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 W wielu interfejsach zwracają ten interfejs najczęściej, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Jest również używany często [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) interfejsu także, jak informacje rozwiązania punktu przerwania.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metod na [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfejsu, ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Pobiera kontekst dokumentu, który odnosi się do kontekstu aktywnego kodu.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Pobiera informacje o języku dla tego kontekstu kodu.|

## <a name="remarks"></a>Uwagi
 Główną różnicą między `IDebugCodeContext2` interfejsu i [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfejsu jest fakt, że `IDebugCodeContext2` zawsze jest wyrównany do instrukcji. Oznacza to, że `IDebugCodeContext2` zawsze wskazuje początek instrukcji, natomiast `IDebugMemoryContext2` mogą wskazywać na dowolny bajt pamięci w architekturze czasu wykonywania. `IDebugCodeContext2` jest zwiększany, zgodnie z instrukcjami opisanymi, a nie według rozmiaru magazynu podstawowego (zazwyczaj bajtów).

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)