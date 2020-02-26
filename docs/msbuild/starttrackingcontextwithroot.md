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
ms.openlocfilehash: 36b48529f82a908ea765151561a71c58cd2c7bc5
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578418"
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