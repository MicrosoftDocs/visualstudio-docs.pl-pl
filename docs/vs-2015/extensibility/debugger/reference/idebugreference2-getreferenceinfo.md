---
title: 'IDebugReference2:: GetReferenceInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77cccb562db79d9f6a53113bda0c4434e19c6813
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155826"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera strukturę [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) , która opisuje odwołanie. Zarezerwowane do użytku w przyszłości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 podczas Kombinacja flag z wyliczenia [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) , która określa pola do wypełnienia w strukturze [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .  
  
 `nRadix`  
 podczas Podstawy do użycia podczas formatowania wszelkich informacji numerycznych.  
  
 `dwTimeout`  
 podczas Maksymalny czas oczekiwania (w milisekundach) przed powrotem z tej metody. Użyj `INFINITE` , aby czekać w nieskończoność.  
  
 `rgpArgs`  
 podczas Tablica obiektów [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) . Zarezerwowane do użytku w przyszłości; Ustaw wartość null.  
  
 `dwArgCount`  
 podczas Liczba argumentów odwołania w `rgpArgs` tablicy. Zarezerwowane do użytku w przyszłości; Ustaw wartość 0.  
  
 `pReferenceInfo`  
 określoną Struktura [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) , która jest wypełniana opisem właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość `E_NOTIMPL`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
