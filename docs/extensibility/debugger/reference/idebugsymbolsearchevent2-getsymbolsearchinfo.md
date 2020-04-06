---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be498154a8141c61f114682893d0aaf8b841cf95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718889"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Wywoływany przez program obsługi zdarzeń, aby pobrać wyniki dotyczące procesu ładowania symbolu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>Parametry
`pModule`\
[na zewnątrz] Obiekt IDebugModule3 reprezentujący moduł, dla którego zostały załadowane symbole.

`pbstrDebugMessage`\
[w, na zewnątrz] Zwraca ciąg zawierający wszelkie komunikaty o błędach z modułu. Jeśli nie ma żadnego błędu, ten ciąg będzie zawierał tylko nazwę modułu, ale nigdy nie jest pusty.

> [!NOTE]
> [C++] `pbstrDebugMessage` nie `NULL` może być i `SysFreeString`musi zostać uwolniony za pomocą .

`pdwModuleInfoFlags`\
[na zewnątrz] Kombinacja flag z [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) wyliczenia wskazujące, czy zostały załadowane symbole.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy program obsługi odbiera [zdarzenie IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) po próbie załadowania symboli debugowania dla modułu, program obsługi można wywołać thismethod, aby określić wyniki tego obciążenia.

## <a name="see-also"></a>Zobacz też
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
