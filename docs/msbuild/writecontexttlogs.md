---
title: WriteContextTLogs | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 722d8c42786a7aaa2daae293b96f7926abcc90ca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62777847"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
Zapisuje pliki dziennika dla bieżącego kontekstu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametry
[in] `intermediateDirectory`

 Katalog, w którym mają zostać zapisane w dzienniku śledzenia.

[in] `tlogRootName`

 Nazwa głównej nazwy pliku dziennika.

## <a name="return-value"></a>Wartość zwracana
 **HRESULT** z **Powodzenie** bitu, jeśli kontekst śledzenia został utworzony.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *FileTracker.h*

## <a name="see-also"></a>Zobacz także
- [WriteAllTLogs](../msbuild/writealltlogs.md)