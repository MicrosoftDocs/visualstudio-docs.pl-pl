---
title: SetThreadCount | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa SetThreadCount do ustawiania liczby wątków globalnych i przypisz tę liczbę do bieżącego wątku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01bfdae1dcd11d7df042948308c424b7773b3bb0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048317"
---
# <a name="setthreadcount"></a>SetThreadCount

Ustawia liczbę wątków globalnych i przypisuje liczbę do bieżącego wątku.

## <a name="syntax"></a>Składnia

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Parametry

podczas `threadCount`

 Liczba wątków, które mają być używane.

## <a name="return-value"></a>Wartość zwracana

 **Wynik HRESULT** z ustawionym **bitem** bitu, jeśli licznik wątków został zaktualizowany.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker. h*