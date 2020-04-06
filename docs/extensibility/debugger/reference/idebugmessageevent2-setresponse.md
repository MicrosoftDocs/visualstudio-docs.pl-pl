---
title: IDebugMessageEvent2::SetResponse | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0ca743deac3e7e635d378f8172ddb4c7e39c72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727392"
---
# <a name="idebugmessageevent2setresponse"></a>IDebugMessageEvent2::SetResponse
Ustawia odpowiedź, jeśli istnieje, z okna komunikatu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetResponse( 
   DWORD dwResponse
);
```

```csharp
int SetResponse( 
   uint dwResponse
);
```

## <a name="parameters"></a>Parametry
`dwResponse`\
[w] Określa odpowiedź, przy użyciu konwencji funkcji Win32. `MessageBox` Szczegółowe informacje można znaleźć w funkcji [AfxMessageBox.](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [Afxmessagebox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
