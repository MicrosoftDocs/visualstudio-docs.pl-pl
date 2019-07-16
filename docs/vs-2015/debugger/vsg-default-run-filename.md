---
title: VSG_DEFAULT_RUN_FILENAME | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2980d34028c58a6abadb2df21bf22c8d37cda6e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160761"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiuje domyślną nazwę pliku pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Nazwa pliku nadaną domyślnie plik dziennika grafiki podczas przechwytywania informacji graficznych programowo.  
  
## <a name="value"></a>Wartość  
 Plik dziennika ciąg literału, który reprezentuje nazwę pliku w oknie grafiki. Domyślnie L"default.vsglog".  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli symbol preprocesora `DONT_SAVE_VSGLOG_TO_TEMP` jest zdefiniowany, następnie nazwa pliku jest określana względem bieżącego katalogu przechwyconych aplikacji lub jest ścieżką bezwzględną; w przeciwnym razie jest określana względem katalogu plików tymczasowych użytkownika i nie może być ścieżką bezwzględną.  
  
 Aby zmienić nazwę pliku zdefiniowane, trzeba będzie ponownie zdefiniować je przed wprowadzeniem `vsgcapture.h` w programach.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano sposób zmiany pliku przechwytywania domyślnej nazwy pliku:  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)
