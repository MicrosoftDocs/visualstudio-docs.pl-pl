---
description: Definiuje domyślną nazwę pliku dziennika grafiki.
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf80b34ed496f06b4051a6e6a9d7d771885e1e45
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232469"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Definiuje domyślną nazwę pliku dziennika grafiki.

## <a name="syntax"></a>Składnia

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parametry
 `filename` Nazwa pliku nadana domyślnie plikowi dziennika grafiki podczas programowego przechwytywania informacji graficznych.

## <a name="value"></a>Wartość
 Literał ciągu reprezentujący nazwę pliku dziennika grafiki. Domyślnie L"default.vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Uwagi
 Jeśli symbol preprocesora jest zdefiniowany, nazwa pliku jest względna względem bieżącego katalogu przechwyconej aplikacji lub jest ścieżką bezwzględną; w przeciwnym razie jest względna względem katalogu plików tymczasowych użytkownika i nie może być ścieżką `DONT_SAVE_VSGLOG_TO_TEMP` bezwzględną.

 Aby zmienić zdefiniowaną nazwę pliku, należy ją ponownie zdefiniować przed dodaniem `vsgcapture.h` jej do programu.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak zmienić domyślną nazwę pliku przechwytywania:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Zobacz też
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
