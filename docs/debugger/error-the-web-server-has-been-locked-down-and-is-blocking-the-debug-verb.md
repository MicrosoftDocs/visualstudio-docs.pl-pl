---
title: 'Błąd: Serwer sieci Web został zablokowany i blokuje czasownik DEBUG | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22a564da1de8a7f375209ff4c02236a3e2baca8f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043097"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Błąd: Serwer sieci Web został zablokowany i blokuje czasownik DEBUG
Przechodzenie do aplikacji sieci Web lub usługi sieci Web XML nie powiodło się, ponieważ uruchomiono narzędzia blokady usług IIS i URLScan został zainstalowany i aktywowany. Ten warunek blokuje usług IIS z otrzymywania czasownik DEBUG.

 URLScan to narzędzie zabezpieczeń, który działa w połączeniu z narzędzia blokady usług IIS, aby zapewnić możliwość Wyłącz niepotrzebne funkcje i ograniczenia typu żądania HTTP, które serwer przetworzy Administratorzy witryn sieci Web usług IIS. Blokując określone żądania HTTP, narzędzia zabezpieczeń dotyczące narzędzia URLScan zapobiega potencjalnie szkodliwych żądań z uzyskiwaniem dostępu do serwera i uszkodzenia.

 Jeśli aplikacja jest uruchomiona w usługach IIS 6.0 w systemie Windows Server 2003, nie muszą działać narzędzia blokady usług IIS, ponieważ usług IIS 6.0 zapewnia taką samą funkcjonalność.

### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Aby włączyć debugowanie na serwerze sieci Web za pomocą narzędzia URLScan zainstalowany

1. Zlokalizuj plik Urlscan.ini. Zwykle znajduje się on w katalogu, który wygląda następująco:

     C:\WINNT\System32\Inetsrv\urlscan

2. Tworzenie kopii pliku i nadaj mu nazwę **Urlscan.old**.

3. Otwórz oryginalną kopię pliku Urlscan.ini za pomocą Notatnika lub ulubionego edytora tekstu.

4. W Urlscan.ini Zlokalizuj sekcję [AllowVerbs]. Dodaj debugowania do sekcji [AllowVerbs]. Jeśli widzisz; debugowanie w sekcji [AllowVerbs], Usuń średnik do usuń znaczniki komentarza zlecenie.

5. Zlokalizuj sekcję [DenyVerbs]. Jeśli debugowania pojawia się w sekcji [DenyVerbs], należy go usunąć.

6. Zapisz plik.

7. Uruchom ponownie serwer lub ponownego uruchomienia usług IIS.

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Błąd: Serwer internetowy nie mógł znaleźć żądanego zasobu](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)