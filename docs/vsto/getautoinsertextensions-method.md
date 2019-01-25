---
title: GetAutoInsertExtensions, metoda
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: debe61f07a8aa8711f1bb0b75ff0c2b39a528b21
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875839"
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
