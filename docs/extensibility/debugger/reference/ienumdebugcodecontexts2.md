---
title: IEnumDebugCodeContexts2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6917c44bb3ddc80513e7c45a6aa4ea0207fd46c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717273"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Ten interfejs wylicza konteksty kodu skojarzone z sesją debugowania lub z określonym programem lub dokumentem.

## <a name="syntax"></a>Składnia

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania listy kontekstów kodu dla określonej pozycji tekstu w programie lub listy kontekstów kodu dla kontekstu określonego dokumentu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [EnumCodeContexts,](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) aby uzyskać ten interfejs reprezentujący listę kontekstów kodu dla określonej pozycji tekstowej w dokumencie źródłowym programu.

 Wywołanie [EnumCodeContexts,](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) aby uzyskać ten interfejs reprezentujący listę wszystkich kontekstów kodu w określonym dokumencie źródłowym.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IEnumDebugCodeContexts2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Pobiera określoną liczbę kontekstów kodu w sekwencji wyliczenia.|
|[Pominąć](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Pomija określoną liczbę kontekstów kodu w sekwencji wyliczenia.|
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Resetuje sekwencję wyliczenia do początku.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Tworzy wyliczenia, który zawiera ten sam stan wyliczenia jako bieżącego wylicznika.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Pobiera liczbę kontekstów kodu w wyliczacza.|

## <a name="remarks"></a>Uwagi
 Visual Studio wywołuje [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) wypełnić listę kontekstów kodu użytkownik może wybrać podczas ustawiania następnej instrukcji lub pokazano demontażu pliku źródłowego. Wiele kontekstów kodu może wystąpić, na przykład, gdy istnieje wiele wystąpień szablonu w stylu C ++.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
