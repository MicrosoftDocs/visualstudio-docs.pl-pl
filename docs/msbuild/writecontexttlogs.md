---
title: WriteContextTLogs | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630708"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs

Zapisuje pliki dzienników dla bieżącego kontekstu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametry

[in] `intermediateDirectory`

 Katalog, w którym ma być przechowywany dziennik śledzenia.

[in] `tlogRootName`

 Nazwa głównego pliku dziennika.

## <a name="return-value"></a>Wartość zwracana

 **Wynik HRESULT** z **pomyślnym** bitem ustawionym w przypadku utworzenia kontekstu śledzenia.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker. h*

## <a name="see-also"></a>Zobacz też

- [WriteAllTLogs](../msbuild/writealltlogs.md)