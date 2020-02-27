---
title: StartTrackingContext | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632111"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

Rozpocznij kontekst śledzenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parametry

[in] `intermediateDirectory`

 Katalog, w którym ma być przechowywany dziennik śledzenia.

[in] `taskName`

 Identyfikuje kontekst śledzenia. Ta nazwa jest używana do tworzenia nazwy pliku dziennika.

## <a name="return-value"></a>Wartość zwracana

 **Wynik HRESULT** z **pomyślnym** bitem ustawionym w przypadku utworzenia kontekstu śledzenia.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker. h*
