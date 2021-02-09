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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9c3d745f14185d46dce08d46b8c56391b108627d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882411"
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
