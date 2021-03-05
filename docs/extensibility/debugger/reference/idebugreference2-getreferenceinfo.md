---
description: Pobiera strukturę DEBUG_REFERENCE_INFO, która opisuje odwołanie.
title: 'IDebugReference2:: GetReferenceInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef953ccde844ac7a2fb5289affaf381f56af8719
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168927"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Pobiera strukturę [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) , która opisuje odwołanie. Zarezerwowane do użytku w przyszłości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetReferenceInfo ( 
   DEBUGREF_INFO_FLAGS   dwFields,
   DWORD                 nRadix,
   DWORD                 dwTimeout,
   IDebugReference2**    rgpArgs,
   DWORD                 dwArgCount,
   DEBUG_REFERENCE_INFO* pReferenceInfo
);
```

```csharp
int GetReferenceInfo ( 
   enum_DEBUGREF_INFO_FLAGS  dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_REFERENCE_INFO[]    pReferenceInfo
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
podczas Kombinacja flag z wyliczenia [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) , która określa pola do wypełnienia w strukturze [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .

`nRadix`\
podczas Podstawy do użycia podczas formatowania wszelkich informacji numerycznych.

`dwTimeout`\
podczas Maksymalny czas oczekiwania (w milisekundach) przed powrotem z tej metody. Użyj `INFINITE` , aby czekać w nieskończoność.

`rgpArgs`\
podczas Tablica obiektów [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) . Zarezerwowane do użytku w przyszłości; Ustaw wartość null.

`dwArgCount`\
podczas Liczba argumentów odwołania w `rgpArgs` tablicy. Zarezerwowane do użytku w przyszłości; Ustaw wartość 0.

`pReferenceInfo`\
określoną Struktura [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) , która jest wypełniana opisem właściwości.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca wartość `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz też
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
