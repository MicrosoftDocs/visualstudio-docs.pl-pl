---
description: Ten interfejs reprezentuje pozycję początkową instrukcji kodu.
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 228b6e84ca2f85803c4a248b966698b822bb572f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164100"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Ten interfejs reprezentuje pozycję początkową instrukcji kodu. W przypadku większości architektur w czasie wykonywania dzisiaj, kontekst kodu może być uważany za adres w strumieniu wykonywania programu.

## <a name="syntax"></a>Składnia

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania implementuje ten interfejs, aby powiązać pozycję instrukcji kodu z pozycją dokumentu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Metody w wielu interfejsach zwracają ten interfejs, zazwyczaj [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Jest on również używany w szerokim zakresie z interfejsem [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) oraz informacjami o rozdzielczości punktu przerwania.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod interfejsu [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Pobiera kontekst dokumentu odnoszący się do aktywnego kontekstu kodu.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Pobiera informacje o języku dla tego kontekstu kodu.|

## <a name="remarks"></a>Uwagi
 Kluczową różnicą między `IDebugCodeContext2` interfejsem i interfejsem [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) jest to, że `IDebugCodeContext2` jest zawsze wyrównany do instrukcji. Oznacza to, że `IDebugCodeContext2` zawsze wskazuje na początek instrukcji, podczas gdy `IDebugMemoryContext2` może wskazywać dowolny bajt pamięci w architekturze czasu wykonywania. `IDebugCodeContext2` jest zwiększany przez instrukcje, a nie podstawowy rozmiar magazynu (zazwyczaj bajt).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
