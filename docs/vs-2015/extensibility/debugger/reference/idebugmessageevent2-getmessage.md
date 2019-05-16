---
title: IDebugMessageEvent2::GetMessage | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14eb540962db3a806273d5c76facb7f9bf25dee7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685896"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera komunikat do wyświetlenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [out] Zwraca typ wiadomości, za pomocą Konwencji Win32 `MessageBox` funkcji. Zobacz [AfxMessageBox](https://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) funkcji, aby uzyskać szczegółowe informacje.  
  
 `pbstrHelpFileName`  
 [out w] Zwraca nazwę pliku pomocy. Może być wartością null (C++) lub wartość pustą (C#), jeśli nie ma żadnego pliku pomocy.  
  
 `pdwHelpId`  
 [out w] Zwraca identyfikator pomocy. Mogą być 0, jeśli pomoc nie jest skojarzone z tym komunikatem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](https://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8)
