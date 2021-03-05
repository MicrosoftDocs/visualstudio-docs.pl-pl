---
description: Określa, czy plik dziennika grafiki jest zapisywany w katalogu plików tymczasowych użytkownika.
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 06152c79859a34e604ffc4e5227e2dd11ebbeaca
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146200"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Określa, czy plik dziennika grafiki jest zapisywany w katalogu plików tymczasowych użytkownika.

## <a name="syntax"></a>Składnia

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Wartość
 Symbol preprocesora, który jest obecny w obecności lub nieobecności, określa, czy plik dziennika grafiki jest zapisywany w katalogu plików tymczasowych użytkownika. Jeśli ten symbol jest zdefiniowany, nazwa pliku zdefiniowana przez jest określana `VSG_DEFAULT_RUN_FILENAME` względem bieżącego katalogu przechwyconej aplikacji lub jest ścieżką bezwzględną; w przeciwnym razie nazwa pliku zdefiniowana przez jest określana `VSG_DEFAULT_RUN_FILENAME` względem katalogu plików tymczasowych użytkownika i nie może być ścieżką bezwzględną.

## <a name="remarks"></a>Uwagi
 W zależności od uprawnień użytkownika plik dziennika grafiki może nie być w stanie zapisać w dowolnej lokalizacji. Zalecamy zapisanie dzienników grafiki w katalogu plików tymczasowych użytkownika lub w innej znanej dobrej lokalizacji, jeśli nie masz pewności, czy wybrana lokalizacja może zostać zapisana przez użytkownika.

 Aby uniemożliwić zapisywanie pliku dziennika grafiki w katalogu plików tymczasowych, należy zdefiniować `DONT_SAVE_VSGLOG_TO_TEMP` przed dołączeniem `vsgcapture.h` .

## <a name="example"></a>Przykład
 Ten przykład pokazuje, jak zapisać plik dziennika grafiki w ścieżce bezwzględnej na komputerze-hoście.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Zobacz też
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
