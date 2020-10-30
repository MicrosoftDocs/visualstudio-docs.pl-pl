---
title: SuspendTracking | Microsoft Docs
description: Poznaj składnię, wymagania i wartość zwracaną dla programu MSBuild SuspendTracking, która wstrzymuje śledzenie w bieżącym kontekście.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 164e1a11c7d107bf1d98419d77fdc50ed353f93b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048093"
---
# <a name="suspendtracking"></a>SuspendTracking

Wstrzymuje śledzenie w bieżącym kontekście.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Wartość zwracana

 **Wynik HRESULT** z **pomyślnym** ustawieniem bitu, jeśli śledzenie zostało zawieszone.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker. h*

## <a name="see-also"></a>Zobacz też

- [ResumeTracking](../msbuild/resumetracking.md)