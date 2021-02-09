---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8aff9836570b3af882e5863cc85834f5423f890e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861429"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Określa domyślną nazwę pliku dziennika grafiki.

## <a name="syntax"></a>Składnia

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parametry
 `filename` Nazwa pliku, która jest domyślnie określona w pliku dziennika grafiki, gdy dane graficzne są przechwytywane programowo.

## <a name="value"></a>Wartość
 Literał ciągu, który reprezentuje nazwę pliku dziennika grafiki. Domyślnie L "default. vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Uwagi
 Jeśli jest zdefiniowany symbol preprocesora `DONT_SAVE_VSGLOG_TO_TEMP` , nazwa pliku jest odnosi się do bieżącego katalogu przechwyconej aplikacji lub jest ścieżką bezwzględną; w przeciwnym razie odnosi się do katalogu plików tymczasowych użytkownika i nie może być ścieżką bezwzględną.

 Aby zmienić zdefiniowaną nazwę pliku, należy ją przedefiniować przed dołączeniem `vsgcapture.h` do programu.

## <a name="example"></a>Przykład
 Ten przykład pokazuje, jak zmienić domyślną nazwę pliku przechwytywania:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Zobacz też
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)