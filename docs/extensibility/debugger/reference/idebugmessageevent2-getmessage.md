---
title: IDebugMessageEvent2::GetMessage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3acce7d8ee50983f24430dca8e1974732b79ad6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945681"
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
  
#### <a name="parameters"></a>Parametry  
 `pMessageType`  
 [out] Zwraca wartość z zakresu od [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) wyliczenie opisujące typ komunikatu.  
  
 `pbstrMessage`  
 [out] Zwraca komunikat.  
  
 `pdwType`  
 [out] Zwraca typ wiadomości, za pomocą Konwencji Win32 `MessageBox` funkcji. Zobacz [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) funkcji, aby uzyskać szczegółowe informacje.  
  
 `pbstrHelpFileName`  
 [out w] Zwraca nazwę pliku pomocy. Może być wartością null (C++) lub wartość pustą (C#), jeśli nie ma żadnego pliku pomocy.  
  
 `pdwHelpId`  
 [out w] Zwraca identyfikator pomocy. Mogą być 0, jeśli pomoc nie jest skojarzone z tym komunikatem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)