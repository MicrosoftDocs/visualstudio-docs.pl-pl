---
description: Ta funkcja uruchamia sekwencję wsadową operacji kontroli źródła.
title: SccBeginBatch, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 08b9199b98e566a71bfeb95124ebd85781e69950
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904763"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch, funkcja
Ta funkcja uruchamia sekwencję wsadową operacji kontroli źródła. [SccEndBatch](../extensibility/sccendbatch-function.md) zostanie wywołany, aby zakończyć partię. Te partie mogą nie być zagnieżdżone.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie rozpoczęto partię operacji.|
|SCC_E_UNKNOWNERROR|Nieokreślona awaria.|

## <a name="remarks"></a>Uwagi
 Partie kontroli źródła są używane do wykonywania tych samych operacji w wielu projektach lub wielu kontekstach. Partie mogą służyć do eliminowania nadmiarowych okien dialogowych dla poszczególnych projektów ze strony użytkownika podczas operacji wsadowych. Funkcja `SccBeginBatch` i [SccEndBatch](../extensibility/sccendbatch-function.md) są używane jako para funkcji, aby wskazać początek i koniec operacji. Nie mogą być zagnieżdżone. `SccBeginBatch` Ustawia flagę wskazującą, że operacja wsadowa jest w toku.

 Podczas działania operacji wsadowej wtyczka kontroli źródła powinna przedstawiać co najwyżej jedno okno dialogowe dla każdego pytania użytkownika i stosować odpowiedź z tego okna dialogowego dla wszystkich kolejnych operacji.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
