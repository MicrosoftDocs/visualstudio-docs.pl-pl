---
title: IDebugCoreServer3::EnableAutoAttach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0823c64e150d306d4613a8df797f11c0785ba762
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774500"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Umożliwia automatyczne dołączanie aparatów określonego debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametry  
 `rgguidSpecificEngines`  
 [in] Tablica identyfikatorów GUID dla każdego silnika debugowania, aby oznaczyć jako automatyczne dołączanie.  
  
 `celtSpecificEngines`  
 [in] Liczba aparatów określone w `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] Początkowy adres URL do użycia podczas dołączania automatycznie.  
  
 `pbstrSessionID`  
 [out] Identyfikator sesji, który został dołączony do automatycznie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Jeden kod błędu: `E_AUTO_ATTACH_NOT_REGISTERED`, co oznacza, że fabryki klas auto-attach nie został zarejestrowany.  
  
## <a name="remarks"></a>Uwagi  
 Po uruchomieniu program skojarzony z określonym adresem URL, aparaty debugowania określonego są pracę i automatycznie dołączone.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

