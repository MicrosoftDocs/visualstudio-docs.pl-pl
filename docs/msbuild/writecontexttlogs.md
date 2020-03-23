---
title: WriteContextTLogs | Dokumenty firmy Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf34ff63b00cf523ba9ef704f4417be4d5cdbf77
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630708"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs

Zapisuje pliki dzienników dla bieżącego kontekstu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametry

[w]`intermediateDirectory`

 Katalog, w którym ma być przechowywane dziennik śledzenia.

[w]`tlogRootName`

 Nazwa główna nazwy pliku dziennika.

## <a name="return-value"></a>Wartość zwracana

 **HRESULT** z **bitem SUCCEEDED** ustawiony, jeśli kontekst śledzenia został utworzony.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker.h*

## <a name="see-also"></a>Zobacz też

- [WriteAllTLogs](../msbuild/writealltlogs.md)