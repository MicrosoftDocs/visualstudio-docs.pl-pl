---
title: Przykład Dia2dump — | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197589"
---
# <a name="dia2dump-sample"></a>Dia2dump — Przykład
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Przykład Dia2dump — jest instalowany z programem Visual Studio i zawiera plik źródłowy Dia2dump —. cpp. Skompilowany plik wykonywalny jest uruchamiany z wiersza polecenia i wyświetla zawartość całego pliku bazy danych programu (. pdb).  
  
### <a name="to-install-the-sample"></a>Aby zainstalować przykład  
  
1. Sprawdź, czy system spełnia wszystkie wymagania dotyczące konfiguracji opisane na stronie startowej Instalatora programu Visual Studio.  
  
2. Zainstaluj program Visual Studio i wykonaj wszystkie instrukcje instalacji i instalacji dla dołączonych przykładów.  
  
#### <a name="to-build-the-sample"></a>Aby skompilować przykład  
  
1. Otwórz plik Dia2dump —. sln w programie Visual Studio. (W razie potrzeby program Visual Studio najpierw pomoże uaktualnić projekt Dia2dump —).  
  
2. Na stronie właściwości projektu w obszarze **ogólne** &#124; &#124; **C/C++** **Dodaj** `..\DIA SDK\include` katalog. Gwarantuje to, że kompilator może znaleźć plik dia2. h.  
  
3. W menu **kompilacja** kliknij polecenie **Kompiluj ponownie rozwiązanie**.  
  
4. Zamknij program Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1. Otwórz wiersz polecenia i wpisz następujące polecenie:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik źródłowy Dia2dump —. cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Porady: rozwiązywanie problemów z nieudanymi aktualizacjami projektu Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)
