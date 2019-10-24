---
title: 'Błąd: serwer sieci Web został zablokowany i blokuje czasownik debugowania | Microsoft Docs'
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
ms.openlocfilehash: 9564f077a5379f44d2beb4d7851453dd6b35fa48
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736952"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Błąd: serwer sieci Web został zablokowany i blokuje zlecenie DEBUG
Przechodzenie do aplikacji sieci Web lub usługi sieci Web XML nie powiodło się, ponieważ uruchomiono narzędzie blokowania usług IIS, a program URLScan został zainstalowany i aktywowany. Ten warunek blokuje otrzymywanie zlecenia DEBUG przez usługi IIS.

 URLScan to narzędzie zabezpieczeń, które działa w połączeniu z narzędziem blokowania usług IIS, dzięki czemu administratorzy witryny sieci Web usług IIS mogą wyłączyć niepotrzebne funkcje i ograniczyć typ żądań HTTP, które serwer będzie przetwarzać. Blokując określone żądania HTTP, narzędzie Security URLScan uniemożliwia potencjalnie szkodliwe żądania docierające do serwera i powodując uszkodzenie.

 Jeśli aplikacja jest uruchomiona w usługach IIS 6,0 w systemie Windows Server 2003, nie trzeba uruchamiać narzędzia blokowania usług IIS, ponieważ usługi IIS 6,0 oferują te same funkcje.

### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Aby włączyć debugowanie na serwerze sieci Web z zainstalowanym programem URLScan

1. Znajdź plik URLScan. ini. Zwykle znajduje się w katalogu, który wygląda następująco:

     C:\WINNT\System32\Inetsrv\urlscan

2. Utwórz kopię pliku i nadaj jej nazwę **URLScan. old**.

3. Otwórz oryginalną kopię pliku URLScan. ini za pomocą Notatnika lub wybranego edytora tekstu.

4. W pliku URLScan. ini Znajdź sekcję [AllowVerbs]. Dodaj debugowanie do sekcji [AllowVerbs]. Jeśli widzisz;D EBUG w sekcji [AllowVerbs], usuń średnik, aby usunąć komentarz do zlecenia.

5. Znajdź sekcję [DenyVerbs]. Jeśli debugowanie pojawi się w sekcji [DenyVerbs], usuń je.

6. Zapisz plik.

7. Uruchom ponownie serwer lub Uruchom ponownie usługi IIS.

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji internetowych: błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Błąd: Serwer internetowy nie mógł znaleźć żądanego zasobu](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)