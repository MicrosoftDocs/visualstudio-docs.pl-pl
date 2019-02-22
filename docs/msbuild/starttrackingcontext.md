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
ms.openlocfilehash: cd0033e189706ee999876a5554e61b1c85eb48ef
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618812"
---
# <a name="starttrackingcontext"></a>StartTrackingContext
Rozpocznij kontekst śledzenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parametry
- [in] `intermediateDirectory` Katalog, w którym mają zostać zapisane w dzienniku śledzenia.

- [in] `taskName` Identyfikuje kontekst śledzenia. Ta nazwa jest używana do tworzenia nazwy pliku dziennika.

## <a name="return-value"></a>Wartość zwracana
 **HRESULT** z **Powodzenie** bitu, jeśli kontekst śledzenia został utworzony.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *FileTracker.h*