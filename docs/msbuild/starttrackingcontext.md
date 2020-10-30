---
title: StartTrackingContext | Microsoft Docs
description: Informacje o parametrach, wymaganiach i wartości zwracanej dla programu MSBuild StartTrackingContext, który uruchamia kontekst śledzenia.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 13a22e3a20b69f62fe1e7d6c8e97eb80df6de1b6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048158"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

Rozpocznij kontekst śledzenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parametry

podczas `intermediateDirectory`

 Katalog, w którym ma być przechowywany dziennik śledzenia.

podczas `taskName`

 Identyfikuje kontekst śledzenia. Ta nazwa jest używana do tworzenia nazwy pliku dziennika.

## <a name="return-value"></a>Wartość zwracana

 **Wynik HRESULT** z **pomyślnym** bitem ustawionym w przypadku utworzenia kontekstu śledzenia.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker. h*
