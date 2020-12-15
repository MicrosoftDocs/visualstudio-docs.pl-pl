---
title: SetWefProcessId, Metoda
description: Dowiedz się, w jaki sposób Metoda SetWefProcessId zapewnia identyfikator procesu, który będzie uruchamiał zawartość WEF (Web Extensions Framework).
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 523279d70215af90ea070ea8272a5221d9947582
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524317"
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
