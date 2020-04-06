---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fec5b8fbe1cae18b8221702fe14443df231d8880
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732954"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Próbuje ustalić, dlaczego automatyczne dołączanie nie powiodło się.

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
[w] Nie jest obecnie używany; zawsze powinna być ustawiona na wartość null.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Poniżej przedstawiono inne typowe kody zwrotów:

|Code|Opis|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Nie można ustalić, dlaczego serwer zdalny nie może uruchomić debugowania.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Nie można debugować na serwerze zdalnym, prawdopodobnie z powodu niewystarczających uprawnień lub ponieważ zlecenie DEBUG nie jest włączone.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Serwer sieci web został zablokowany i blokuje zlecenie DEBUG, które jest wymagane do włączenia debugowania.|

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
