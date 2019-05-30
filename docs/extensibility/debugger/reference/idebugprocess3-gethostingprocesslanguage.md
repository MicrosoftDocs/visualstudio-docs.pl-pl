---
title: IDebugProcess3::GetHostingProcessLanguage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::GetHostingProcessLanguage
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36098cf1fa19228962743856a814f0d094439edd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313902"
---
# <a name="idebugprocess3gethostingprocesslanguage"></a>IDebugProcess3::GetHostingProcessLanguage
Ta metoda zwraca `GUID` reprezentujący język tego procesu według stawki ustalonej przez wywołanie [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md).

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetHostingProcessLanguage(
   GUID* pguidLang
);
```

```csharp
int GetHostingProcessLanguage(
   out Guid pguidLang
);
```

## <a name="parameters"></a>Parametry
`pguidLang`\
[out] `GUID` Języka tego procesu. `GUID_NULL` (C++) lub `Guid.Empty` (C#) oznacza, że język nie jest ustawiony.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)