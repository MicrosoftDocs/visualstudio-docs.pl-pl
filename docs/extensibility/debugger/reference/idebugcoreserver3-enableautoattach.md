---
description: Włącza automatyczne dołączanie dla określonych aparatów debugowania.
title: 'IDebugCoreServer3:: EnableAutoAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 644d238db11c117b9068de8f7903361b9712f3aa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163151"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Włącza automatyczne dołączanie dla określonych aparatów debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parametry
`rgguidSpecificEngines`\
podczas Tablica identyfikatorów GUID dla każdego aparatu debugowania do oznaczenia jako automatycznego dołączania.

`celtSpecificEngines`\
podczas Liczba aparatów określona w `rgguidSpecificEngines` .

`pszStartPageUrl`\
podczas Początkowy adres URL, który będzie używany podczas dołączania.

`pbstrSessionID`\
określoną Identyfikator sesji, która została dołączona ponownie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Jeden kod błędu to `E_AUTO_ATTACH_NOT_REGISTERED` , co oznacza, że fabryka klas automatycznie dołączanych nie została zarejestrowana.

## <a name="remarks"></a>Uwagi
 Po uruchomieniu programu skojarzonego z określonym adresem URL określone aparaty debugowania są automatycznie uruchamiane i dołączane.

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
