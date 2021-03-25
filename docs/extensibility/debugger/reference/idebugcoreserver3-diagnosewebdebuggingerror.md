---
description: Próbuje określić dlaczego automatyczne dołączanie nie powiodło się.
title: IDebugCoreServer3::D iagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a7e41842842850f7eb9ff4993bba348aea9816f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077710"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Próbuje określić dlaczego automatyczne dołączanie nie powiodło się.

## <a name="syntax"></a>Składnia

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parametry
`pszUrl`\
podczas Obecnie nie używane; zawsze powinna być ustawiona na wartość null.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Oto inne typowe kody powrotne:

|Kod|Opis|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Nie można określić, dlaczego zdalny serwer nie może rozpocząć debugowania.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Nie można debugować na serwerze zdalnym, prawdopodobnie z powodu niewystarczających uprawnień lub że zlecenie debugowania nie jest włączone.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Serwer sieci Web został zablokowany i blokuje czasownik debugowania, który jest wymagany do włączenia debugowania.|

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
