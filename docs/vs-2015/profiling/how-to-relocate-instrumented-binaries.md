---
title: 'Porady: przemieszczanie instrumentowanych plików binarny | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 012236c9d3d02f498843f7a185efdd07c6e96a4d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770856"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Porady: przemieszczanie instrumentowanych plików binarny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas Instrumentacji sondy są wstawiane do plików binarnych do pomiaru wydajności aplikacji. Wybierając Zmień lokalizację instrumentowanych danych binarnych kopię oryginalny plik binarny jest Instrumentacji i umieścić w określonej lokalizacji. Ta opcja jest przydatna, jeśli nie chcesz, aby program profilujący do zmiany nazwy oryginalny plik binarny. Jeśli plik binarny nie został przeniesiony, jest zastępowany oryginalną wersję pliku binarnego.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Aby zmienić lokalizację instrumentowanych danych binarnych  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij **właściwości**.  
  
2.  W **stron właściwości**, kliknij przycisk **binarne** właściwości.  
  
3.  Wybierz **przemieszczanie instrumentowanych plików binarny** pole wyboru.  
  
4.  Określ lokalizację dla instrumentowanego pliku binarnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)



