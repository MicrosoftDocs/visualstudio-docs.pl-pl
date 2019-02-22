---
title: StartTrackingContextWithRoot | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53f2c1ebd5896eaa8a4b9d5ff4e5cb7856a1f8e2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690492"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
Rozpoczyna kontekst śledzenia, przy użyciu pliku odpowiedzi, określając znaczników głównych.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametry
[in] `intermediateDirectory`

 Katalog, w którym mają zostać zapisane w dzienniku śledzenia.

[in] `taskName`

 Identyfikuje kontekst śledzenia. Ta nazwa jest używana do tworzenia nazwy pliku dziennika.

[in] `rootMarkerResponseFile`

 Nazwa ścieżki pliku odpowiedzi, który zawiera znacznik główny. Główna nazwa jest używana do grupy wszystkich śledzenia dla kontekstu wspólnie.

## <a name="return-value"></a>Wartość zwracana
 **HRESULT** z **Powodzenie** bitu, jeśli kontekst śledzenia został utworzony.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *FileTracker.h*

## <a name="see-also"></a>Zobacz także
- [StartTrackingContext](../msbuild/starttrackingcontext.md)