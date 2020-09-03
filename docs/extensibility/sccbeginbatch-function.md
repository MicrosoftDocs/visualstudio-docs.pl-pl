---
title: Funkcja SccBeginBatch | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701199"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch, funkcja
Ta funkcja uruchamia sekwencję wsadową operacji kontroli źródła. [SccEndBatch](../extensibility/sccendbatch-function.md) zostanie wywołana w celu zakończenia zadania wsadowego. Te partie nie mogą być zagnieżdżane.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Partia operacji została pomyślnie rozpoczęta.|
|SCC_E_UNKNOWNERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Partie kontroli źródła są używane do wykonywania tych samych operacji w wielu projektach lub wielu kontekstach. Partie mogą służyć do eliminowania nadmiarowych okien dialogowych na projekt ze środowiska użytkownika podczas operacji wsadowej. `SccBeginBatch`Funkcja i [SccEndBatch](../extensibility/sccendbatch-function.md) są używane jako para funkcji do wskazywania początku i końca operacji. Nie mogą być zagnieżdżane. `SccBeginBatch` ustawia flagę wskazującą, że operacja wsadowa jest w toku.

 Podczas wykonywania operacji wsadowej Wtyczka kontroli źródła powinna mieć co najwyżej jedno okno dialogowe dla każdego pytania do użytkownika i stosować odpowiedź z tego okna dialogowego we wszystkich kolejnych operacjach.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
