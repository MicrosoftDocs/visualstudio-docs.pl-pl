---
title: GetAutoInsertExtensions, metoda
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a12adf6e83e58b877e36dd65d98b617cda3a39b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647213"
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
  
  