---
title: IDebugCodeContext2::GetLanguageInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8e2ecbd9e33eaf43df9937eabd7d9149d3e85f4d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206739"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Pobiera informacje o języku dla tego kontekstu kodu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

## <a name="parameters"></a>Parametry
`pbstrLanguage`\
[out w] Zwraca ciąg, który zawiera nazwę języka, takie jak "C++."

`pguidLanguage`\
[out w] Zwraca identyfikator GUID dla języka kontekst kodu, na przykład `guidCPPLang`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Co najmniej jeden z parametrów musi zwracać wartość inną niż null.

## <a name="see-also"></a>Zobacz także
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)