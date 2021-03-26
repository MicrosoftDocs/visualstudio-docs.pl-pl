---
description: Ta metoda pobiera język, który został użyty do skompilowania kodu pod adresem debugowania.
title: 'IDebugSymbolProvider:: GetLanguage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7bcf2bd16212767fc8eff6106cdb3602bc293c9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086992"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Ta metoda pobiera język, który został użyty do skompilowania kodu pod adresem debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetLanguage( 
   IDebugAddress* pAddress,
   GUID*          pguidLanguage,
   GUID*          pguidLanguageVendor
);
```

```csharp
int GetLanguage(
   IDebugAddress pAddress,
   out Guid      pguidLanguage,
   out Guid      pguidLanguageVendor
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
podczas Obiekt adresu reprezentowany przez interfejs [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pguidLanguage`\
określoną Zwraca wartość określającą `GUID` język.

`pguidLanguageVendor`\
określoną Zwraca wartość określającą `GUID` dostawcę języka.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Aparat debugowania wywołuje tę metodę w celu uzyskania informacji potrzebnych do wybrania prawidłowej ewaluatora wyrażeń.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
