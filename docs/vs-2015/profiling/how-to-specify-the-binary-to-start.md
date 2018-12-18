---
title: 'Porady: Określanie plików binarnych do uruchomienia | Dokumentacja firmy Microsoft'
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
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f3a176ded749f640f2e37f27c9753ee1902772c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777373"
---
# <a name="how-to-specify-the-binary-to-start"></a>Porady: określanie plików binarnych do uruchomienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Do profilu plików binarnych takich jak biblioteki dll, należy wprowadzić informacje w  **\<docelowy > strony właściwości** okno dialogowe. Te informacje wskazują, gdzie znaleźć aplikacji wywołującej projektu DLL.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Określ plik wykonywalny do uruchomienia  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy docelowy plik binarny, a następnie kliknij **właściwości**.  
  
2.  W **stron właściwości** okno dialogowe, kliknij przycisk **Uruchom** właściwości.  
  
3.  Wybierz **zastąpienie właściwości projektu** pole wyboru.  
  
4.  W **pliku wykonywalnego do uruchomienia** tekst pola, określ lokalizację pliku.  
  
5.  W **argumenty** tekstu należy określić argumenty, które są wymagane do uruchamiania aplikacji.  
  
6.  W **katalog roboczy** tekstu określ lokalizację katalogu.  
  
7.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)



