---
title: StartTrackingContextWithRoot | Dokumenty firmy Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68d585361b9797bf1df9c8b0b31f8a089e9de025
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632098"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Rozpoczyna kontekst śledzenia przy użyciu pliku odpowiedzi określającego znacznik główny.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametry

[w]`intermediateDirectory`

 Katalog, w którym ma być przechowywane dziennik śledzenia.

[w]`taskName`

 Identyfikuje kontekst śledzenia. Ta nazwa jest używana do tworzenia nazwy pliku dziennika.

[w]`rootMarkerResponseFile`

 Nazwa ścieżki pliku odpowiedzi zawierającego znacznik główny. Nazwa katalogu głównego służy do grupowania wszystkich śledzenia kontekstu razem.

## <a name="return-value"></a>Wartość zwracana

 **HRESULT** z **bitem SUCCEEDED** ustawiony, jeśli kontekst śledzenia został utworzony.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker.h*

## <a name="see-also"></a>Zobacz też

- [StartTrackingContext](../msbuild/starttrackingcontext.md)