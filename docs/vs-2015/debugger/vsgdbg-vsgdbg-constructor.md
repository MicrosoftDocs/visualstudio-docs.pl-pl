---
title: VsgDbg::VsgDbg (Konstruktor) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056c5f5e19a4d1e025969aa40ad75f3852b4201b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781923"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Konstruktor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworzy wystąpienie klasy `VsgDbg` klasy z lub bez przygotowania diagnostyki grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych domyślnie w oparciu o określony parametr logiczny składnik w aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bDefaultInit`  
 `true` do określenia, to należy przygotować aktywnie przechwytywanie i rejestrowanie informacji graficznych; składnik w aplikacji Narzędzie Diagnostyka grafiki `false` do określenia, że aplikacja nie powinna być przygotowana do aktywnego przechwytywanie i rejestrowanie informacji graficznych w tej chwili.  
  
## <a name="remarks"></a>Uwagi  
 Gdy Konstruktor jest wywoływana z `bDefaultInit` równa `true`, nazwę pliku w pliku dziennika grafiki określają sposób, w jaki `DONT_SAVE_VSGLOG_TO_TEMP` i `VSG_DEFAULT_RUN_FILENAME` symboli preprocesora są zdefiniowane przed `vsgcapture.h` znajduje się w aplikacji.  
  
 Gdy Konstruktor jest wywoływana z `bDefaultInit` równa `false`, składnik w aplikacji Narzędzie Diagnostyka grafiki można przygotować aktywnie przechwytywanie i rejestrowanie informacji graficznych w późniejszym czasie przez wywołanie metody `Init` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [VsgDbg:: ~ VsgDbg (destruktor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)



