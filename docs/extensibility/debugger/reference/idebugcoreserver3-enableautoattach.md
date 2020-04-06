---
title: IDebugCoreServer3::EnableAutoAttach | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732910"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Umożliwia automatyczne dołączanie dla określonych aparatów debugowania.

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
[w] Tablica identyfikatorów GUID dla każdego aparatu debugowania, aby oznaczyć jako automatyczne dołączanie.

`celtSpecificEngines`\
[w] Liczba silników określona w . `rgguidSpecificEngines`

`pszStartPageUrl`\
[w] Początkowy adres URL używany podczas automatycznego dołączania.

`pbstrSessionID`\
[na zewnątrz] Identyfikator sesji, która została automatycznie dołączona.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Jeden kod `E_AUTO_ATTACH_NOT_REGISTERED`błędu to , który wskazuje, że fabryka klasy automatycznego dołączania nie została zarejestrowana.

## <a name="remarks"></a>Uwagi
 Po uruchomieniu programu skojarzonego z określonym adresem URL określone aparaty debugowania są uruchamiane i dołączane.

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
