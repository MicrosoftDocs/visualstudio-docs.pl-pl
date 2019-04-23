---
title: 'Instrukcje: Określanie plików binarnych do uruchomienia | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098431"
---
# <a name="how-to-specify-the-binary-to-start"></a>Instrukcje: Określanie plików binarnych do uruchomienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Do profilu plików binarnych takich jak biblioteki dll, należy wprowadzić informacje w  **\<docelowy > strony właściwości** okno dialogowe. Te informacje wskazują, gdzie znaleźć aplikacji wywołującej projektu DLL.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Określ plik wykonywalny do uruchomienia  
  
1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy docelowy plik binarny, a następnie kliknij **właściwości**.  
  
2. W **stron właściwości** okno dialogowe, kliknij przycisk **Uruchom** właściwości.  
  
3. Wybierz **zastąpienie właściwości projektu** pole wyboru.  
  
4. W **pliku wykonywalnego do uruchomienia** tekst pola, określ lokalizację pliku.  
  
5. W **argumenty** tekstu należy określić argumenty, które są wymagane do uruchamiania aplikacji.  
  
6. W **katalog roboczy** tekstu określ lokalizację katalogu.  
  
7. Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
