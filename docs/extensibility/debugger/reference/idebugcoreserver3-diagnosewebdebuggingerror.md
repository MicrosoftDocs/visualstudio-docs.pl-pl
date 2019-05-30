---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52b6d634da7cda9c7b90b8cd4f7d93e7accc033d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317795"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Próbuje określić, dlaczego auto-attach nie powiodło się.

## <a name="syntax"></a>Składnia

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parametry
`pszUrl`\
[in] Obecnie nieużywane; powinny być zawsze ustawiony na wartość null.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Inne typowe kody powrotu są następujące:

|Kod|Opis|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Nie można ustalić, dlaczego serwera zdalnego nie powiodło się można rozpocząć debugowania.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Nie można debugować na serwerze zdalnym, prawdopodobnie z powodu niewystarczających uprawnień lub ponieważ nie włączono czasownik DEBUG.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Serwer sieci web został zablokowany i blokuje czasownik DEBUG, który jest wymagany do włączenia debugowania.|

## <a name="see-also"></a>Zobacz także
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)