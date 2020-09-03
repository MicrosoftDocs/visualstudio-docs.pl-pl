---
title: 'Błąd: serwer sieci Web został zablokowany i blokuje czasownik debugowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: b85efc44b39485476154d0f41f3261b2aeb1ea7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203209"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Błąd: serwer sieci Web został zablokowany i blokuje zlecenie DEBUG
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przechodzenie do aplikacji sieci Web lub usługi sieci Web XML nie powiodło się, ponieważ uruchomiono narzędzie blokowania usług IIS, a program URLScan został zainstalowany i aktywowany. Ten warunek blokuje otrzymywanie zlecenia DEBUG przez usługi IIS.  
  
 URLScan to narzędzie zabezpieczeń, które działa w połączeniu z narzędziem blokowania usług IIS, dzięki czemu administratorzy witryny sieci Web usług IIS mogą wyłączyć niepotrzebne funkcje i ograniczyć typ żądań HTTP, które serwer będzie przetwarzać. Blokując określone żądania HTTP, narzędzie Security URLScan uniemożliwia potencjalnie szkodliwe żądania docierające do serwera i powodując uszkodzenie.  
  
 Jeśli aplikacja jest uruchomiona w usługach IIS 6,0 w systemie Windows Server 2003, nie trzeba uruchamiać narzędzia blokowania usług IIS, ponieważ usługi IIS 6,0 oferują te same funkcje.  
  
### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Aby włączyć debugowanie na serwerze sieci Web z zainstalowanym programem URLScan  
  
1. Znajdź plik Urlscan.ini. Zwykle znajduje się w katalogu, który wygląda następująco:  
  
     C:\WINNT\System32\Inetsrv\urlscan  
  
2. Utwórz kopię pliku i nadaj jej nazwę **URLScan. old**.  
  
3. Otwórz oryginalną kopię pliku Urlscan.ini przy użyciu Notatnika lub wybranego edytora tekstu.  
  
4. W Urlscan.ini zlokalizuj sekcję [AllowVerbs]. Dodaj debugowanie do sekcji [AllowVerbs]. Jeśli widzisz;D EBUG w sekcji [AllowVerbs], usuń średnik, aby usunąć komentarz do zlecenia.  
  
5. Znajdź sekcję [DenyVerbs]. Jeśli debugowanie pojawi się w sekcji [DenyVerbs], usuń je.  
  
6. Zapisz plik.  
  
7. Uruchom ponownie serwer lub Uruchom ponownie usługi IIS.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Błąd: Serwer internetowy nie mógł znaleźć żądanego zasobu](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)
