---
title: StartTrackingContext | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c395df1e08f1b4e33e9cd34fec54bdd044f3b4c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939212"
---
# <a name="starttrackingcontext"></a>StartTrackingContext
Rozpocznij kontekst śledzenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parametry
[in] `intermediateDirectory`

 Katalog, w którym mają zostać zapisane w dzienniku śledzenia.

[in] `taskName`

 Identyfikuje kontekst śledzenia. Ta nazwa jest używana do tworzenia nazwy pliku dziennika.

## <a name="return-value"></a>Wartość zwracana
 **HRESULT** z **Powodzenie** bitu, jeśli kontekst śledzenia został utworzony.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *FileTracker.h*