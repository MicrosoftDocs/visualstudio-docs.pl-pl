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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b52541c99fa81f31eddde8e6c12ad2eee04f3c20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967049"
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