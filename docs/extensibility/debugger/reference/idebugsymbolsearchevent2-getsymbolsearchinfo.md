---
description: Wywoływane przez procedurę obsługi zdarzeń w celu pobrania wyników procesu ładowania symboli.
title: 'IDebugSymbolSearchEvent2:: GetSymbolSearchInfo — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9f03562f3370268f720b2d8053bbd6a2979f6a19
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145771"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Wywoływane przez procedurę obsługi zdarzeń w celu pobrania wyników procesu ładowania symboli.

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
określoną Obiekt IDebugModule3 reprezentujący moduł, dla którego zostały załadowane symbole.

`pbstrDebugMessage`\
[in. out] Zwraca ciąg zawierający wszystkie komunikaty o błędach z modułu. Jeśli nie ma żadnych błędów, ten ciąg będzie zawierać nazwę modułu, ale nigdy nie jest pusty.

> [!NOTE]
> [C++] `pbstrDebugMessage` nie może być `NULL` i musi być zwolniona z `SysFreeString` .

`pdwModuleInfoFlags`\
określoną Kombinacja flag z wyliczenia [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) wskazująca, czy zostały załadowane wszystkie symbole.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy program obsługi odbiera zdarzenie [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) po wykonaniu próby załadowania symboli debugowania dla modułu, program obsługi może wywołać thismethod, aby określić wyniki tego obciążenia.

## <a name="see-also"></a>Zobacz też
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
