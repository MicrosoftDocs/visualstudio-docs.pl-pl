---
title: SetWefProcessId, Metoda
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
ms.openlocfilehash: 13a6748e2e3b66f581a3c72c1f847e0329189e64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537335"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId, Metoda
  Zawiera identyfikator procesu, który będzie uruchamiał zawartość WEF (Web Extensions Framework).

## <a name="syntax"></a>Składnia

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*dwProcessId*|Identyfikator procesu, który będzie używany do uruchamiania zawartości WEF.|

## <a name="return-value"></a>Wartość zwracana
 Wartość HRESULT wskazująca, czy metoda została ukończona pomyślnie.

## <a name="remarks"></a>Uwagi
 Ta metoda musi być wywoływana po utworzeniu procesu zawartości WEF, ale przed uruchomieniem dowolnego WEF zawartości.

 Jeśli chcesz, aby środowisko programistyczne dołączył debuger do procesu zawartości WEF, środowisko musi wykonać tę operację w implementacji tej metody.
