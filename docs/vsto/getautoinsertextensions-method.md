---
title: GetAutoInsertExtensions, metoda
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9716f6adcee1d443e342074f3c46a57a1ace26db
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915893"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions, metoda
  Pobiera informacje o aplikacjach pakietu Office, które mają być wstawiane automatycznie podczas debugowania.  
  
 Ta metoda jest zarezerwowana do użytku w przyszłości.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*psaExtensionNames*|Rozszerzenie nazwy aplikacji dla pakietu Office.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Każda aplikacja dla pakietu Office ma zostać wstawiony jest zwracany jako nazwa rozszerzenia aplikacji pakietu Office, który odpowiada wartości w obszarze **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. Host musi wyszukiwać te wartości w rejestrze i automatyczne wstawianie rozszerzenia.  
