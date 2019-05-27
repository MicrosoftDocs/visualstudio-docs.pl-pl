---
title: IDebugCoreServer3::EnableAutoAttach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a1b714856811ccd9b8e95d074cfc95740e27e5f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205521"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Umożliwia automatyczne dołączanie aparatów określonego debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parametry
`rgguidSpecificEngines`\
[in] Tablica identyfikatorów GUID dla każdego silnika debugowania, aby oznaczyć jako automatyczne dołączanie.

`celtSpecificEngines`\
[in] Liczba aparatów określone w `rgguidSpecificEngines`.

`pszStartPageUrl`\
[in] Początkowy adres URL do użycia podczas dołączania automatycznie.

`pbstrSessionID`\
[out] Identyfikator sesji, który został dołączony do automatycznie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Jeden kod błędu: `E_AUTO_ATTACH_NOT_REGISTERED`, co oznacza, że fabryki klas auto-attach nie został zarejestrowany.

## <a name="remarks"></a>Uwagi
 Po uruchomieniu program skojarzony z określonym adresem URL, aparaty debugowania określonego są pracę i automatycznie dołączone.

## <a name="see-also"></a>Zobacz także
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)