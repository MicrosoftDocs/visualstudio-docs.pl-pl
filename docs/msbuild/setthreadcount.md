---
title: SetThreadCount | Microsoft Docs
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
ms.openlocfilehash: 102f46ec639719bb2bec70a38c6c7177c63793c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632332"
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