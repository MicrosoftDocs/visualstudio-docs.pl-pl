---
title: StartTrackingContextWithRoot | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632098"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Uruchamia kontekst śledzenia przy użyciu pliku odpowiedzi określającego znacznik główny.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametry

[in] `intermediateDirectory`

 Katalog, w którym ma być przechowywany dziennik śledzenia.

[in] `taskName`

 Identyfikuje kontekst śledzenia. Ta nazwa jest używana do tworzenia nazwy pliku dziennika.

[in] `rootMarkerResponseFile`

 Nazwa ścieżki pliku odpowiedzi zawierającego znacznik główny. Nazwa główna służy do grupowania wszystkich śledzenia dla kontekstu.

## <a name="return-value"></a>Wartość zwracana

 **Wynik HRESULT** z **pomyślnym** bitem ustawionym w przypadku utworzenia kontekstu śledzenia.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker. h*

## <a name="see-also"></a>Zobacz też

- [StartTrackingContext](../msbuild/starttrackingcontext.md)