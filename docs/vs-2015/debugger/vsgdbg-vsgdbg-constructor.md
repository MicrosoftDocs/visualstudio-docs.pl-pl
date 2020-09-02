---
title: 'VsgDbg:: VsgDbg (Konstruktor) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3bd179aea7d961df6145b7af2f074927fcdc3e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157437"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Konstruktor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Konstruuje wystąpienie `VsgDbg` klasy z lub bez przygotowania składnika w aplikacji diagnostyki grafiki, aby aktywnie przechwytywać i rejestrować informacje graficzne domyślnie na podstawie określonego parametru logicznego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bDefaultInit`  
 `true` Aby określić, że składnik aplikacji diagnostyki grafiki ma być przygotowany do aktywnego przechwytywania i rejestrowania informacji graficznych; `false` Aby określić, że aplikacja nie powinna być przygotowana do aktywnego przechwytywania i rejestrowania informacji graficznych.  
  
## <a name="remarks"></a>Uwagi  
 Gdy Konstruktor jest wywoływany z `bDefaultInit` ustawionym na `true` , nazwa pliku dziennika grafiki jest określana na podstawie tego, jak `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` symbole i preprocesora są zdefiniowane zanim `vsgcapture.h` zostanie uwzględniony w aplikacji.  
  
 Gdy Konstruktor jest wywoływany z `bDefaultInit` ustawionym na `false` , składnik w aplikacji diagnostyki grafiki może być przygotowany do aktywnego przechwytywania i rejestrowania informacji graficznych w późniejszym czasie przez wywołanie `Init` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [VsgDbg:: ~ VsgDbg (destruktor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
