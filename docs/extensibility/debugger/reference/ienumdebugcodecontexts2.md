---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dae1261adca25162b5bb81cc3ae8b006ce7ef283
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350885"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Ten interfejs wylicza kontekstów kod związany z sesji debugowania lub z określonego programu lub dokumentu.

## <a name="syntax"></a>Składnia

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania listę konteksty kodu dla określonego tekstu pozycji w programie lub Podaj listę konteksty kodu dla kontekstu określonego dokumentu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) uzyskać ten interfejs reprezentujący listę konteksty kodu dla pozycji określony tekst w dokumencie źródłowym programu.

 Wywołaj [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) uzyskać ten interfejs reprezentujący listę wszystkich kontekstach kodu w określonego dokumentu źródłowego.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IEnumDebugCodeContexts2`.

|Metoda|Opis|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Pobiera określoną liczbę kontekstów kodu w kolejności wyliczenia.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Pomija określoną liczbę kontekstów kodu w kolejności wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Resetuje sekwencji wyliczenia na początku.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Pobiera liczbę kontekstów kodu w moduł wyliczający.|

## <a name="remarks"></a>Uwagi
 Visual Studio wywołania [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) do wypełnienia listy kontekstów kod użytkownika mogą wybierać kiedy ustawienie następnej instrukcji lub wyświetlanie dezasemblacji dla pliku źródłowego. Wiele kontekstów kod może wystąpić na przykład, gdy istnieje wiele wystąpień szablonu styl C++.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)