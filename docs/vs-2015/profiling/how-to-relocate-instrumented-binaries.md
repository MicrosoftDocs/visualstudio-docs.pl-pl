---
title: 'Instrukcje: Zmienianie położenia plików binarnych w Instrumentacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 00b39b91b0a776438199d1df3c212cb9fe40f338
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155521"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Porady: przemieszczanie instrumentowanych plików binarny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas Instrumentacji sondy są wstawiane do pliku binarnego w celu zmierzenia wydajności aplikacji. Po wybraniu przeniesienia pliku binarnego z instrumentacją kopia oryginalnego pliku binarnego zostaje przyprowadzona i umieszczona w określonej lokalizacji. Ta opcja jest przydatna, jeśli nie chcesz, aby Profiler zmienił nazwę oryginalnego pliku binarnego. Jeśli plik binarny nie zostanie przeniesiony, oryginalna wersja pliku binarnego zostanie nadpisywana.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Aby przenieść plik binarny z instrumentacją  
  
1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.  
  
2. Na **stronie właściwości**kliknij właściwości **binarne** .  
  
3. Zaznacz pole wyboru **Przenieś instrumentację plików binarnych** .  
  
4. Określ lokalizację pliku binarnego Instrumentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)
