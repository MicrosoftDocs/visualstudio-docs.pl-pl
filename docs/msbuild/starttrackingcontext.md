---
title: Kontekst StartTrackinga | Dokumenty firmy Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50f62704897d68b0e323b948b8f4ed7e96a10c9a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632111"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

Rozpocznij kontekst śledzenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parametry

[w]`intermediateDirectory`

 Katalog, w którym ma być przechowywane dziennik śledzenia.

[w]`taskName`

 Identyfikuje kontekst śledzenia. Ta nazwa jest używana do tworzenia nazwy pliku dziennika.

## <a name="return-value"></a>Wartość zwracana

 **HRESULT** z **bitem SUCCEEDED** ustawiony, jeśli kontekst śledzenia został utworzony.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker.h*
