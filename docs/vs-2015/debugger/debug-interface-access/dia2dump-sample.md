---
title: Dia2dump — przykład | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 727d7a4a97bc0aa55d370a45549941ab286930f9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805401"
---
# <a name="dia2dump-sample"></a>Dia2dump — Przykład
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dia2dump — przykład został zainstalowany przy użyciu programu Visual Studio i zawiera plik źródłowy Dia2dump.cpp. Skompilowany plik wykonywalny jest uruchamiane z wiersza polecenia i wyświetla zawartość pliku bazy danych (PDB) całego programu.  
  
### <a name="to-install-the-sample"></a>Aby zainstalować przykład  
  
1.  Sprawdź, czy system spełnia wszystkie wymagania dotyczące konfiguracji opisanych w strony początkowej Instalatora programu Visual Studio.  
  
2.  Zainstaluj program Visual Studio i wykonaj wszystkie ustawienia i instrukcje dotyczące instalacji załączone przykłady.  
  
#### <a name="to-build-the-sample"></a>Aby skompilować przykład  
  
1.  Otwórz plik Dia2dump.sln w programie Visual Studio. (Jeśli to konieczne, program Visual Studio najpierw pomoże Ci uaktualnić projekt dia2dump —.)  
  
2.  Na stronach właściwości projektu w **C/C++** &#124; **ogólne** &#124; **dodatkowe katalogi dołączenia** właściwości, określ `..\DIA SDK\include` katalogu. Gwarantuje to, że kompilator może odnaleźć pliku dia2.h.  
  
3.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
4.  Zamknij program Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz wiersz polecenia i wpisz następujące polecenie:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik źródłowy Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Instrukcje: rozwiązywanie problemów z nieudanymi uaktualnieniami projektu programu Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)



