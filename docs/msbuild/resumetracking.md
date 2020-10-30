---
title: ResumeTracking | Microsoft Docs
description: Poznaj składnię, wymagania i wartość zwracaną dla programu MSBuild ResumeTracking, która wznawia śledzenie w bieżącym kontekście.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9af7c90342638fb0c154e7de21fa111d560905d0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048426"
---
# <a name="resumetracking"></a>ResumeTracking

Wznawia śledzenie w bieżącym kontekście.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Wartość zwracana

 **Wynik HRESULT** z **pomyślnie** ustawionym bitem, jeśli śledzenie zostało wznowione. **E_FAIL** jest zwracany, jeśli nie można wznowić śledzenia, ponieważ kontekst nie jest dostępny.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker. h*

## <a name="see-also"></a>Zobacz też

- [SuspendTracking](../msbuild/suspendtracking.md)