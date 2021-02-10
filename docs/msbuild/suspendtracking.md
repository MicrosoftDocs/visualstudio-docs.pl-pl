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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e8be768bc48c1815fc00069640e5bf3f4370f434
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945282"
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