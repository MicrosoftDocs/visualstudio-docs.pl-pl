---
title: IDebugReference2::SetValueAsString | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c8414ce5f53acec2a30ff681ff0bab8ddc919310
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720295"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
Ustawia wartość odwołania z ciągu. Zarezerwowane do użytku w przyszłości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   DWORD     dwRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   dwRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Parametry
`pszValue`\
[w] Wartość jako ciąg.

`dwRadix`\
[w] Radix do wykorzystania w formatowaniu wszelkich informacji liczbowych.

`dwTimeout`\
[w] Maksymalny czas ( w milisekundach) oczekiwania przed zwróceniem tej metody. Służy `INFINITE` do oczekiwania przez czas nieokreślony.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca wartość `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz też
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
