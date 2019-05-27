---
title: IDebugMessageEvent2::SetResponse | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea35bcdef843756124fe7102167e35694d9fa1b4
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210348"
---
# <a name="idebugmessageevent2setresponse"></a>IDebugMessageEvent2::SetResponse
Ustawia odpowiedzi, jeśli występują w oknie komunikatu.

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
[in] Określa odpowiedź, za pomocą Konwencji Win32 `MessageBox` funkcji. Zobacz [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) funkcji, aby uzyskać szczegółowe informacje.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)