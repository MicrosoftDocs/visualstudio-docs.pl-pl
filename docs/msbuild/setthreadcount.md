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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f7282b8c4589007492e48994628910b3a4ef0691
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966165"
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