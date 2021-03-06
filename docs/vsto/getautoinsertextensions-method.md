---
description: Pobiera informacje o aplikacjach pakietu Office, które mają być automatycznie wstawiane podczas debugowania.
title: GetAutoInsertExtensions, Metoda
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c4a49942f50a79db604d2363cf2d85762c5ddce5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223436"
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
 Każda aplikacja pakietu Office, która ma zostać wstawiona, jest zwracana jako nazwa rozszerzenia aplikacji pakietu Office, która odnosi się do wartości w obszarze **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. Host musi odszukać te wartości w rejestrze, a następnie automatycznie wstawić rozszerzenia.
