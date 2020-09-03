---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732910"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Włącza automatyczne dołączanie dla określonych aparatów debugowania.

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
