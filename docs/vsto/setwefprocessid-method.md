---
title: SetWefProcessId, metoda
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
ms.openlocfilehash: 1352ccc9318061be4a2f9ad2da7d63715acd6721
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978358"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId, metoda
  Zawiera identyfikator procesu, który uruchomi zawartości w ramach rozszerzenia sieci Web (WEF).

## <a name="syntax"></a>Składnia

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*dwProcessId*|Identyfikator procesu, który będzie służyć do uruchamiania WEF zawartości.|

## <a name="return-value"></a>Wartość zwracana
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.

## <a name="remarks"></a>Uwagi
 Ta metoda musi zostać wywołana, po utworzeniu procesu zawartości WEF, ale przed uruchomieniem żadnej zawartości WEF.

 Jeśli chcesz dołączyć debuger do procesu zawartości WEF przez środowisko deweloperskie, środowisko musi wykonać tej operacji w danej implementacji tej metody.
