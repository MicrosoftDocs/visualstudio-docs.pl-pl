---
title: Dia2dump — przykład | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a817720c1ad73b666e0c9a586bb583120a2533c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197589"
---
# <a name="dia2dump-sample"></a>Dia2dump — Przykład
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dia2dump — przykład został zainstalowany przy użyciu programu Visual Studio i zawiera plik źródłowy Dia2dump.cpp. Skompilowany plik wykonywalny jest uruchamiane z wiersza polecenia i wyświetla zawartość pliku bazy danych (PDB) całego programu.  
  
### <a name="to-install-the-sample"></a>Aby zainstalować przykład  
  
1. Sprawdź, czy system spełnia wszystkie wymagania dotyczące konfiguracji opisanych w strony początkowej Instalatora programu Visual Studio.  
  
2. Zainstaluj program Visual Studio i wykonaj wszystkie ustawienia i instrukcje dotyczące instalacji załączone przykłady.  
  
#### <a name="to-build-the-sample"></a>Aby skompilować przykład  
  
1. Otwórz plik Dia2dump.sln w programie Visual Studio. (Jeśli to konieczne, program Visual Studio najpierw pomoże Ci uaktualnić projekt dia2dump —.)  
  
2. Na stronach właściwości projektu w **C/C++** &#124; **ogólne** &#124; **dodatkowe katalogi dołączenia** właściwości, określ `..\DIA SDK\include` katalogu. Gwarantuje to, że kompilator może odnaleźć pliku dia2.h.  
  
3. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
4. Zamknij program Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1. Otwórz wiersz polecenia i wpisz następujące polecenie:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik źródłowy Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Instrukcje: rozwiązywanie problemów z nieudanymi aktualizacjami projektu Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)
