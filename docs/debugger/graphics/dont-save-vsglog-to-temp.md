---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 967ff50991efbbd7b598605abd992b298367d01c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006180"
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Definiuje jego obecność czy plik dziennika grafiki jest zapisywany do katalogu plików tymczasowych użytkownika.  

## <a name="syntax"></a>Składnia  

```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  

## <a name="value"></a>Wartość  
 Symbol preprocesora, który zgodnie z jego obecność lub brak Określa, czy plik dziennika grafiki są zapisywane w katalogu plików tymczasowych użytkownika. Jeśli ten symbol jest zdefiniowana, a następnie nazwę pliku, zdefiniowane przez `VSG_DEFAULT_RUN_FILENAME` względem bieżącego katalogu przechwyconych aplikacji lub jest ścieżką bezwzględną; w przeciwnym razie nazwa pliku zdefiniowane przez `VSG_DEFAULT_RUN_FILENAME` jest określana względem katalogu plików tymczasowych użytkownika i nie może być Ścieżka bezwzględna.  

## <a name="remarks"></a>Uwagi  
 W zależności od uprawnień użytkownika plik dziennika grafiki nie może być można zapisać w dowolne miejsce. Zaleca się, że użytkownik nie chce zapisać dzienniki grafiki do katalogu plików tymczasowych użytkownika lub w innej lokalizacji znanego dobrego, jeśli wiesz, czy mogą być zapisywane lokalizacji, należy wybrać przez użytkownika.  

 Aby zapobiec sytuacji, w której plik dziennika grafiki są zapisywane w katalogu plików tymczasowych, muszą zdefiniowane `DONT_SAVE_VSGLOG_TO_TEMP` przed wprowadzeniem `vsgcapture.h`.  

## <a name="example"></a>Przykład  
 Ten przykład przedstawia sposób zapisać plik dziennika grafiki ścieżką bezwzględną na komputerze hosta.  

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  

#include <vsgcapture.h>  
```  

## <a name="see-also"></a>Zobacz też  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
