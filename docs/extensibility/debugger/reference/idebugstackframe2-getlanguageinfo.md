---
title: IDebugStackFrame2::GetLanguageInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 90fd7beabb14163558afe4b957d95635e91f904a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719551"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo
Pobiera język skojarzone z tą ramką stosu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

#### <a name="parameters"></a>Parametry
 `pbstrLanguage`

 [out] Zwraca nazwę języka, który implementuje metodę skojarzoną z tą ramką stosu.

 `pguidLanguage`

 [out] Zwraca `GUID` języka. Aby uzyskać [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] języków, na przykład, następujące mogą zostać zwrócone:

-   `guidVBScriptLang`

-   `guidJScriptLang`

-   `guidCPPLang`

-   `guidVBLang`

-   `guidSQLLang`

-   `guidScriptLang`

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)