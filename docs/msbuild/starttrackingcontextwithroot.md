---
title: StartTrackingContextWithRoot | Microsoft Docs
description: Dowiedz się, jak używać programu MSBuild StartTrackingContextWithRoot do uruchamiania kontekstu śledzenia przy użyciu pliku odpowiedzi określającego znacznik główny.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ccca75a0fe525c4e1d9f421b2264070ebda9bdf3
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048135"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Uruchamia kontekst śledzenia przy użyciu pliku odpowiedzi określającego znacznik główny.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametry

podczas `intermediateDirectory`

 Katalog, w którym ma być przechowywany dziennik śledzenia.

podczas `taskName`

 Identyfikuje kontekst śledzenia. Ta nazwa jest używana do tworzenia nazwy pliku dziennika.

podczas `rootMarkerResponseFile`

 Nazwa ścieżki pliku odpowiedzi zawierającego znacznik główny. Nazwa główna służy do grupowania wszystkich śledzenia dla kontekstu.

## <a name="return-value"></a>Wartość zwracana

 **Wynik HRESULT** z **pomyślnym** bitem ustawionym w przypadku utworzenia kontekstu śledzenia.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker. h*

## <a name="see-also"></a>Zobacz też

- [StartTrackingContext](../msbuild/starttrackingcontext.md)