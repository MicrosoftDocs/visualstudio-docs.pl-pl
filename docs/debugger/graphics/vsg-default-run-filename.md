---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 835e2cec19e36418091e094abd2ec76bd6403398
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734828"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Określa domyślną nazwę pliku dziennika grafiki.

## <a name="syntax"></a>Składnia

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parametry
 `filename` nazwę pliku, która jest domyślnie określona w pliku dziennika grafiki, gdy dane graficzne są przechwytywane programowo.

## <a name="value"></a>Wartość
 Literał ciągu, który reprezentuje nazwę pliku dziennika grafiki. Domyślnie L "default. vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Uwagi
 Jeśli zostanie zdefiniowany symbol preprocesora `DONT_SAVE_VSGLOG_TO_TEMP`, nazwa pliku jest określana względem bieżącego katalogu przechwyconej aplikacji lub jest ścieżką bezwzględną; w przeciwnym razie odnoszą się do katalogu plików tymczasowych użytkownika i nie może być ścieżką bezwzględną.

 Aby zmienić zdefiniowaną nazwę pliku, należy ją przedefiniować przed dołączeniem `vsgcapture.h` do programu.

## <a name="example"></a>Przykład
 Ten przykład pokazuje, jak zmienić domyślną nazwę pliku przechwytywania:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Zobacz także
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)