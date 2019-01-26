---
title: VSG_DEFAULT_RUN_FILENAME | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af34aed1ed99e1d8e51e594a514286caa7adf748
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979923"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
Definiuje domyślną nazwę pliku pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Nazwa pliku nadaną domyślnie plik dziennika grafiki podczas przechwytywania informacji graficznych programowo.  
  
## <a name="value"></a>Wartość  
 Plik dziennika ciąg literału, który reprezentuje nazwę pliku w oknie grafiki. Domyślnie L"default.vsglog".  
  
```C++  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli symbol preprocesora `DONT_SAVE_VSGLOG_TO_TEMP` jest zdefiniowany, następnie nazwa pliku jest określana względem bieżącego katalogu przechwyconych aplikacji lub jest ścieżką bezwzględną; w przeciwnym razie jest określana względem katalogu plików tymczasowych użytkownika i nie może być ścieżką bezwzględną.  
  
 Aby zmienić nazwę pliku zdefiniowane, trzeba będzie ponownie zdefiniować je przed wprowadzeniem `vsgcapture.h` w programach.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano sposób zmiany pliku przechwytywania domyślnej nazwy pliku:  
  
```C++  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)