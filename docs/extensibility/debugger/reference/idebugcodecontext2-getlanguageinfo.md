---
title: IDebugCodeContext2::GetLanguageInfo | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 465cc07b3ca75835afe0737fb22ba403acc4098b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734244"
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
[w, na zewnątrz] Zwraca ciąg zawierający nazwę języka, na przykład "C++".

`pguidLanguage`\
[w, na zewnątrz] Zwraca identyfikator GUID dla języka kontekstu kodu, `guidCPPLang`na przykład .

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Co najmniej jeden z parametrów musi zwracać wartość niekwaśną.

## <a name="see-also"></a>Zobacz też
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
