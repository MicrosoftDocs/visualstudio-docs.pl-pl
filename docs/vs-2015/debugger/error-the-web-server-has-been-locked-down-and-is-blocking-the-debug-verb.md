---
title: 'Błąd: Serwer sieci Web został zablokowany i blokuje czasownik DEBUG | Dokumentacja firmy Microsoft'
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
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 9c8c4812-17db-484d-9c1b-ffd9e3bfef5a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60fffd146516bca57497bfdaaabe0f51407063b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770246"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Błąd: serwer sieci Web został zablokowany i blokuje zlecenie DEBUG
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przechodzenie do aplikacji sieci Web lub usługi sieci Web XML nie powiodło się, ponieważ uruchomiono narzędzia blokady usług IIS i URLScan został zainstalowany i aktywowany. Ten warunek blokuje usług IIS z otrzymywania czasownik DEBUG.  
  
 URLScan to narzędzie zabezpieczeń, który działa w połączeniu z narzędzia blokady usług IIS, aby zapewnić możliwość Wyłącz niepotrzebne funkcje i ograniczenia typu żądania HTTP, które serwer przetworzy Administratorzy witryn sieci Web usług IIS. Blokując określone żądania HTTP, narzędzia zabezpieczeń dotyczące narzędzia URLScan zapobiega potencjalnie szkodliwych żądań z uzyskiwaniem dostępu do serwera i uszkodzenia.  
  
 Jeśli aplikacja jest uruchomiona w usługach IIS 6.0 w systemie Windows Server 2003, nie muszą działać narzędzia blokady usług IIS, ponieważ usług IIS 6.0 zapewnia taką samą funkcjonalność.  
  
### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Aby włączyć debugowanie na serwerze sieci Web za pomocą narzędzia URLScan zainstalowany  
  
1.  Zlokalizuj plik Urlscan.ini. Zwykle znajduje się on w katalogu, który wygląda następująco:  
  
     C:\WINNT\System32\Inetsrv\urlscan  
  
2.  Tworzenie kopii pliku i nadaj mu nazwę **Urlscan.old**.  
  
3.  Otwórz oryginalną kopię pliku Urlscan.ini za pomocą Notatnika lub ulubionego edytora tekstu.  
  
4.  W Urlscan.ini Zlokalizuj sekcję [AllowVerbs]. Dodaj debugowania do sekcji [AllowVerbs]. Jeśli widzisz; debugowanie w sekcji [AllowVerbs], Usuń średnik do usuń znaczniki komentarza zlecenie.  
  
5.  Zlokalizuj sekcję [DenyVerbs]. Jeśli debugowania pojawia się w sekcji [DenyVerbs], należy go usunąć.  
  
6.  Zapisz plik.  
  
7.  Uruchom ponownie serwer lub ponownego uruchomienia usług IIS.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Błąd: Serwer internetowy nie mógł znaleźć żądanego zasobu](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)



