---
title: 'Instrukcje: Określanie pliku binarnego do uruchomienia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 919e84393cf4aef929a504aadbefe905afe24bfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203430"
---
# <a name="how-to-specify-the-binary-to-start"></a>Porady: określanie plików binarnych do uruchomienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby profilować pliki binarne, takie jak biblioteki DLL, należy wprowadzić informacje w oknie dialogowym ** \<Target> strony właściwości** . Te informacje wskazują, gdzie projekt DLL może znaleźć aplikację wywołującą.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Aby określić plik wykonywalny do uruchomienia  
  
1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy docelowy plik binarny, a następnie kliknij polecenie **Właściwości**.  
  
2. W oknie dialogowym **strony właściwości** kliknij przycisk właściwości **uruchamiania** .  
  
3. Zaznacz pole wyboru **Zastąp właściwości projektu** .  
  
4. W polu tekstowym **plik wykonywalny do uruchomienia** Określ lokalizację pliku.  
  
5. W polu tekstowym **argumenty** określ argumenty wymagane do uruchomienia aplikacji.  
  
6. W polu tekstowym **katalog roboczy** Określ lokalizację katalogu.  
  
7. Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
