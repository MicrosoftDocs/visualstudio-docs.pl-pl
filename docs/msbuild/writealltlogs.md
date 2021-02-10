---
title: WriteAllTLogs | Microsoft Docs
description: Poznaj składnię, wymagania i wartość zwracaną dla WriteAllTLogs, która zapisuje dzienniki śledzenia dla wszystkich wątków i kontekstów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65e0610c8148ab6ff32d8c19f6fd378ba46d76d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933599"
---
# <a name="writealltlogs"></a>WriteAllTLogs

Zapisuje dzienniki śledzenia dla wszystkich wątków i kontekstów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametry

podczas `intermediateDirectory`

 Katalog, w którym ma być przechowywany dziennik śledzenia.

podczas `tlogRootName`

 Nazwa głównego pliku dziennika.

## <a name="return-value"></a>Wartość zwracana

 **Wynik HRESULT** z **pomyślnym** bitem ustawionym w przypadku utworzenia kontekstu śledzenia.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker. h*

## <a name="see-also"></a>Zobacz też

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)