---
title: WriteAllTLogs | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eadb30ee25b1182be5deb12feebd5ef280ebf4b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77630681"
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