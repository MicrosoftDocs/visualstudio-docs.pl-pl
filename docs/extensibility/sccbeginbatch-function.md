---
title: Funkcja SccBeginBatch | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701199"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch, funkcja
Ta funkcja uruchamia sekwencję partii operacji kontroli źródła. [SccEndBatch](../extensibility/sccendbatch-function.md) zostanie wywołana do zakończenia partii. Te partie nie mogą być zagnieżdżone.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Partia operacji została pomyślnie rozpoczęta.|
|SCC_E_UNKNOWNERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 Partie kontroli źródła są używane do wykonywania tych samych operacji w wielu projektach lub wielu kontekstach. Partie mogą służyć do wyeliminowania nadmiarowych okien dialogowych na projekt z środowiska użytkownika podczas operacji wsadowej. Funkcja `SccBeginBatch` i [SccEndBatch](../extensibility/sccendbatch-function.md) są używane jako para funkcji, aby wskazać początek i koniec operacji. Nie można ich zagnieździć. `SccBeginBatch`ustawia flagę wskazującą, że trwa operacja wsadowa.

 Podczas operacji wsadowej jest w mocy, wtyczki kontroli źródła powinien przedstawić co najwyżej jedno okno dialogowe dla dowolnego pytania do użytkownika i zastosować odpowiedź z tego okna dialogowego na wszystkie kolejne operacje.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
