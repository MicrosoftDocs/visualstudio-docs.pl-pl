---
description: Ta funkcja zawiera partię operacji kontroli źródła.
title: Funkcja SccEndBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f4ea8ec19fcfe55da0666383408c2addbd42f2e6
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221577"
---
# <a name="sccendbatch-function"></a>SccEndBatch, funkcja
Ta funkcja zawiera partię operacji kontroli źródła. Te partie nie mogą być zagnieżdżane.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Partia operacji została zakończona pomyślnie.|
|SCC_E_UNKNOWNERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Partie kontroli źródła są używane do wykonywania tych samych operacji kontroli źródła w wielu projektach lub wielu kontekstach. Za pomocą partii można wyeliminować nadmiarowe okna dialogowe ze środowiska użytkownika podczas operacji wsadowej. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) i `SccEndBatch` Funkcja są używane jako para do wskazywania początku i końca operacji. Nie mogą być zagnieżdżane.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
