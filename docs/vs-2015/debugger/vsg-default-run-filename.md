---
title: VSG_DEFAULT_RUN_FILENAME | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07407dc0a50da935d8d5a9fa0eed213633adbe4f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801059"
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



