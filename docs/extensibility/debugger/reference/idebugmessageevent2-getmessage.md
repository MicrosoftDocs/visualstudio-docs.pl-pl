---
title: 'IDebugMessageEvent2:: GetMessage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8e1b1d379f235729614f257e38ea2b84b856507b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851052"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Pobiera komunikat do wyświetlenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMessage( 
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrMessage,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetMessage( 
   out enum_MESSAGETYPE pMessageType,
   out string           pbstrMessage,
   out uint             pdwType,
   out string           pbstrHelpFileName,
   out uint             dwHelpId
);
```

## <a name="parameters"></a>Parametry
`pMessageType`\
określoną Zwraca wartość z wyliczenia [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) opisującą typ komunikatu.

`pbstrMessage`\
określoną Zwraca komunikat.

`pdwType`\
określoną Zwraca typ komunikatu przy użyciu konwencji `MessageBox` funkcji Win32. Zobacz funkcję [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) , aby uzyskać szczegółowe informacje.

`pbstrHelpFileName`\
[in. out] Zwraca nazwę pliku pomocy. Może mieć wartość null (C++) lub pustą (C#), jeśli nie ma pliku pomocy.

`pdwHelpId`\
[in. out] Zwraca identyfikator pomocy. Może mieć wartość 0, jeśli nie ma pomocy skojarzonej z tym komunikatem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
