---
title: IDebugMessageEvent2::GetMessage | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 819b796a656f0ef8775fbb1c9e800e3019b81729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727397"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Pobiera komunikat, który ma być wyświetlany.

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
[na zewnątrz] Zwraca wartość z wyliczenia [MESSAGETYPE,](../../../extensibility/debugger/reference/messagetype.md) który opisuje typ wiadomości.

`pbstrMessage`\
[na zewnątrz] Zwraca wiadomość.

`pdwType`\
[na zewnątrz] Zwraca typ wiadomości, przy użyciu konwencji funkcji Win32. `MessageBox` Szczegółowe informacje można znaleźć w funkcji [AfxMessageBox.](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)

`pbstrHelpFileName`\
[w, na zewnątrz] Zwraca nazwę pliku pomocy. Może to być wartość null (C++) lub pusta (C#), jeśli nie ma pliku pomocy.

`pdwHelpId`\
[w, na zewnątrz] Zwraca identyfikator pomocy. Może być 0, jeśli nie ma pomocy związanej z tym komunikatem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [Afxmessagebox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
