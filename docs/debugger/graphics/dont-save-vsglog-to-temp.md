---
description: Określa, czy plik dziennika grafiki jest zapisywany w katalogu plików tymczasowych użytkownika.
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bbf7fa453f36c861d632fc17e46e003e568008db
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232690"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Określa, czy plik dziennika grafiki jest zapisywany w katalogu plików tymczasowych użytkownika.

## <a name="syntax"></a>Składnia

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Wartość
 Symbol preprocesora, który przez jego obecność lub brak określa, czy plik dziennika grafiki jest zapisywany w katalogu plików tymczasowych użytkownika. Jeśli ten symbol jest zdefiniowany, nazwa pliku zdefiniowana przez jest względna względem bieżącego katalogu przechwyconej aplikacji lub jest ścieżką bezwzględną. W przeciwnym razie nazwa pliku zdefiniowana przez element jest względna dla katalogu plików tymczasowych użytkownika i nie może być ścieżką `VSG_DEFAULT_RUN_FILENAME` `VSG_DEFAULT_RUN_FILENAME` bezwzględną.

## <a name="remarks"></a>Uwagi
 W zależności od uprawnień użytkownika plik dziennika grafiki może nie być możliwe do zapisania w dowolnej lokalizacji. Zalecamy zapisywanie dzienników graficznych w katalogu plików tymczasowych użytkownika lub w innej znanej dobrej lokalizacji, jeśli nie masz pewności, czy lokalizacja, w którym chcesz wybrać, może być zapisywana przez użytkownika.

 Aby zapobiec zapisywaniu pliku dziennika grafiki w katalogu plików tymczasowych, należy zdefiniować przed `DONT_SAVE_VSGLOG_TO_TEMP` dodaniem pliku `vsgcapture.h` .

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak zapisać plik dziennika grafiki w ścieżce bezwzględnej na maszynie hosta.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Zobacz też
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
