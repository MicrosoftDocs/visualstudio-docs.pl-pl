---
title: GetAutoInsertExtensions, Metoda
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f5d88af6f24306b7b243359c9797a2cb7e7449bc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543510"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions, Metoda
  Pobiera informacje o aplikacjach pakietu Office, które mają być automatycznie wstawiane podczas debugowania.

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
|*psaExtensionNames*|Nazwy rozszerzeń aplikacji pakietu Office.|

## <a name="return-value"></a>Wartość zwracana
 Wartość HRESULT wskazująca, czy metoda została ukończona pomyślnie.

## <a name="remarks"></a>Uwagi
 Każda aplikacja pakietu Office, która ma zostać wstawiona, jest zwracana jako nazwa rozszerzenia aplikacji pakietu Office, która odnosi się do wartości w obszarze **HKEY_CURRENT_USER \software\microsoft\office\wef\developer**. Host musi odszukać te wartości w rejestrze, a następnie automatycznie wstawić rozszerzenia.
