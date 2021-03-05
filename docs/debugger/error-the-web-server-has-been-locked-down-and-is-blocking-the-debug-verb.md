---
description: Przechodzenie do aplikacji sieci Web lub usługi sieci Web XML nie powiodło się, ponieważ uruchomiono narzędzie blokowania usług IIS, a program URLScan został zainstalowany i aktywowany.
title: Serwer sieci Web został zablokowany i blokuje czasownik debugowania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: def2ecc4e0ae5285976f8d6cd8b98a2446a8881c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146538"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Błąd: serwer sieci Web został zablokowany i blokuje zlecenie DEBUG
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
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Błąd: Serwer internetowy nie mógł znaleźć żądanego zasobu](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)
