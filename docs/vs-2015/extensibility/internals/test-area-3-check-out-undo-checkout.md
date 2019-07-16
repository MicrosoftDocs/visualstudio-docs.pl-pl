---
title: 'Obszar testowy 3: Wyewidencjonowanie i cofanie wyewidencjonowania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab4389c936b71ba8ccbb21b22d0a5e533282026d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156000"
---
# <a name="test-area-3-check-outundo-checkout"></a>Obszar testowy 3: Zapoznaj się z / Cofnij wyewidencjonowanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ten obszar testowy wtyczki kontroli źródła obejmuje edycji oraz przywracanie elementów z magazynu wersji za pomocą **Wyewidencjonuj** i **Cofnij wyewidencjonowanie** poleceń.  
  
 **Zapoznaj się z**: Wyewidencjonowano element w magazynie wersji jako znaki modyfikuje kopii lokalnej do odczytu/zapisu.  
  
 **Cofnij wyewidencjonowanie**: Zaewidencjonowano element w magazynie wersji jako znaki przywraca kopii lokalnej do stanu przed wyewidencjonowanie (w zależności od opcji).  
  
## <a name="command-menu-access"></a>Dostęp do Menu polecenia  
 Następujące [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ścieżki menu środowiska zintegrowanego rozwoju są używane w przypadkach testowych.  
  
##### <a name="check-out"></a>Wymelduj się:  
  
- **Plik**, **kontroli źródła**, **zapoznaj się z**.  
  
- **Plik**, **zapoznaj się z**.  
  
- Menu skrótów **zapoznaj się z**.  
  
- Cofnij wyewidencjonowanie: **Plik**, **kontroli źródła**, **Cofnij wyewidencjonowanie**.  
  
## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie.  
  
- Po operacji wyewidencjonowania plików docelowych i/lub foldery są oznaczone jako wyewidencjonowane z magazynu wersji.  
  
- Magazyn wersji atrybuty wyewidencjonowanie do odpowiednich użytkowników.  
  
- Data i Godzina wyewidencjonowania są prawidłowe (ustawienia dla każdego użytkownika).  
  
## <a name="test-cases"></a>Przypadki testowe  
 Poniżej przedstawiono określonych przypadków testowych dla obszaru testu wyewidencjonowania/cofnięcie wyewidencjonowania.  
  
### <a name="case-3a-check-out"></a>Wielkości liter 3a: Wyewidencjonuj  
 Ta sekcja koncentruje się na operację polecenia wyewidencjonowywania.  
  
|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Zapoznaj się z wyłącznych (COE) projekt klienta|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z całego projektu wyłącznie (**pliku**, **Wyewidencjonuj**).|Występuje, sprawdź.|  
|Zapoznaj się wyłącznie (COE) w systemie plików lub lokalny projekt sieci Web usług IIS|1.  Ustaw połączenie z serwerem sieci Web do udziału w plików **narzędzia**, **opcje**, **projektów**, **ustawień sieci Web**.<br />2.  Utwórz projekt sieci Web.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Zapoznaj się z całego projektu wyłącznie (**pliku**, **kontroli źródła**, **Wyewidencjonuj**).|Występuje, sprawdź.|  
|Zapoznaj się z elementów rozwiązania w rozwiązaniu (nowe metody obsługi innych plików)|1.  Utwórz puste rozwiązanie.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z rozwiązania.<br />4.  Dodaj kilka elementów rozwiązania.<br />5.  Zaewidencjonuj nowo dodanych elementów.<br />6.  Zaznaczanie wielu elementów rozwiązania.<br />7.  Zapoznaj się z wybranych elementów (Menu skrótów **Wyewidencjonuj**).|Wybrane pliki są wyewidencjonowane.|  
|Zapoznaj się wersja lokalna (jeśli jest to wtyczka testowanej obsługuje tę funkcję)|1.  Użytkownik 1: Utwórz projekt klienta.<br />2.  Użytkownik 1: Dodaj rozwiązanie do kontroli źródła.<br />3.  Użytkownik 2: Otwórz rozwiązanie z kontroli źródła do innej lokalizacji.<br />4.  Użytkownik 2: Zapoznaj się z plikiem.<br />5.  Użytkownik 2: Zmodyfikuj plik.<br />6.  Użytkownik 2: Sprawdź w pliku.<br />7.  Użytkownik 1: Zapoznaj się z lokalną wersją pliku (Sprawdź **Sprawdź lokalnej wersji** zaawansowanych opcji **Wyewidencjonuj** okno dialogowe).|Wersja lokalna pliku został wyewidencjonowany.<br /><br /> Modyfikacje przez użytkownika 2 nie są stosowane do użytkownika 1 pliku.|  
  
### <a name="case-3b-disconnected-check-out"></a>Wielkość 3b: Wyewidencjonowanie bez połączenia  
 Działający w trybie odłączenia pozwala użytkownikom pewien stopień Lepsza obsługa kontroli źródła ciągłego, gdy nie jest dołączony bezpośrednio do magazynu wersji. Odbywa się lokalnie, buforując wszystkie istotne informacje dotyczące zobowiązaniom rozwiązanie i projekty.  
  
 Wyewidencjonowanie na wyłączność operacji tylko może wystąpić, gdy połączone z magazynu kontroli źródła. Udostępnione wyboru czynności mogą występować w dowolnym momencie, czy połączone lub odłączona. W związku z tym kiedy odłączony od magazynu wersji, tylko **zapoznaj się z udostępnionych** (COS) polecenie jest włączone. Gdy odłączony, **Cofnij wyewidencjonowanie** jest wyłączony, ponieważ nie można pobrać starą wersję zastąpienie zmian wprowadzonych przez użytkownika.  
  
 Po użytkownik połączy się ponownie do wersji przechowywania stanów wyewidencjonowania wszystkich zobowiązaniom rozwiązania i projekty są synchronizowane. Wykonuje niezbędne aktualizacje do magazynu wyewidencjonowania, wykonanych przez użytkownika. Gdy synchronizacja się nie stało, użytkownik będzie mógł kontynuować pracę w zwykły (Połączono).  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
- Nie można użyć **Sprawdź się wyłącznie** polecenia bez połączenia z magazynu wersji.  
  
- Nie można użyć **Cofnij wyewidencjonowanie** polecenia bez połączenia z magazynu wersji.  
  
- **Udostępnione Wyewidencjonuj** polecenie działa.  
  
|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Przy braku połączenia, zapoznaj się z plikiem, a następnie podłącz do synchronizacji|1.  Odłącz projekt pod kontrolą źródła, za pomocą okna dialogowego Zmiana kontroli źródła (**pliku**, **kontroli źródła**, **zmiany źródła Contro**l).<br />2.  Wyewidencjonuj plik.<br />3.  Kliknij polecenie Wyewidencjonuj (odłączony), w oknie dialogowym ostrzeżenia.<br />4.  Edytuj plik.<br />5.  Połącz, za pomocą okna dialogowego Zmiana kontroli źródła.<br />6.  Pobierz najnowszą wersję edytowanego pliku.|Typowe oczekiwane zachowanie.|  
  
### <a name="case-3c-query-editquery-save-qeqs"></a>Przypadek 3c: Edytuj zapytanie/zapytanie Zapisz (QEQS)  
 Edycje, zmiany są śledzone elementy pod kontrolą źródła i zapisuje, pomagając użytkownikom łatwo zarządzać ich pliki. Podczas edycji elementu kontrolowanego, który jest "zaewidencjonowane" QEQS przechwytuje próba edycji i pytaniem, czy chce wyewidencjonować plik, aby go edytować. W zależności od **narzędzia**, **opcje** ustawienia, użytkownik jest zmuszony do sprawdzenia wyjściowy plik, aby móc edytować lub mogły być Edytuj kopię w pamięci i sprawdzić później. Jeśli użytkownik **narzędzia**, **opcje** ustawienie nie jest ustawiona, aby wyświetlić Sprawdź okno dialogowe i po prostu zaznacz go, a następnie jako użytkownik dokona jego edycji, plik automatycznie sprawdza dostępność, jeśli to możliwe.  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
- Po operacji wyewidencjonowania plików docelowych i/lub foldery są oznaczone jako wyewidencjonowane z magazynu wersji.  
  
- Magazyn wersji atrybuty wyewidencjonowanie do odpowiednich użytkowników.  
  
- Data i godzina wyewidencjonowanie są prawidłowe (ustawienia dla każdego użytkownika).  
  
- Lokalna kopia pliku lub folderu docelowego jest zapisywalna.  
  
|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Edytuj plik tekstowy, który jest zaewidencjonowany|1.  Utwórz nowy projekt zawierający plik tekstowy.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Ustaw **narzędzia**, **opcje**, **kontroli źródła**, **Zezwalaj na wyświetlanie plików można edytować, gdy tylko do odczytu na dysku** do niezaznaczone.<br />4.  Ustaw **narzędzia**, **opcje**, **kontroli źródła**, **wybór opcji Monituj o wyewidencjonowanie** w **po zaznaczeniu tej opcji pliki są edytowane** pola kombi.<br />5.  Ustaw **narzędzia**, **opcje**, **kontroli źródła**, **wybór opcji Monituj o wyewidencjonowanie** w **po zaznaczeniu tej opcji pliki są zapisywane** pola kombi.<br />6.  Otwórz plik tekstowy w edytorze, spróbuj wpisać nowy tekst w pliku. Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />7.  Kliknij przycisk **anulować** w **Wyewidencjonuj do edycji** okno dialogowe. Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />8.  Ustaw **narzędzia**, **opcje**, **kontroli źródła**, **Zezwalaj na wyświetlanie plików można edytować, gdy tylko do odczytu na dysku** do zaznaczenia.<br />9. Otwórz plik projektu w edytorze, spróbuj wpisać nowy tekst w pliku. Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />10. Kliknij przycisk **Edytuj** w **Wyewidencjonuj do edycji** okno dialogowe. Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />11. Edytuj plik tekstowy i podjąć próbę zapisania go.|`Result of step 6:`<br /><br /> Zapoznaj się z dla pojawi się okno dialogowe edycji.<br /><br /> `Result of step 7:`<br /><br /> Plik pozostaje niezmieniony.<br /><br /> `Result of step 9:`<br /><br /> Zapoznaj się z dla pojawi się okno dialogowe edycji.<br /><br /> `Result of step 10:`<br /><br /> Możesz edytować plik projektu w pamięci.<br /><br /> `Result of step 11:`<br /><br /> Zapisz, zapoznaj się na zapisywanie okno dialogowe pojawia się na.|  
|Edytuj plik rozwiązania, który jest zaewidencjonowany|Powtórz kroki opisane w poprzednim testu, ale zamiast modyfikowania pliku tekstowego, zmodyfikuj rozwiązania, zmieniając właściwości rozwiązania.|Takie same jak poprzedni test|  
|Edytuj plik projektu, który jest zaewidencjonowany|Powtórz kroki opisane w poprzednim testu, ale zamiast modyfikowania pliku tekstowego, zmodyfikuj projektu, zmieniając właściwości projektu.|Tak samo jak poprzedni test.|  
  
### <a name="case-3d-silent-check-out"></a>Zamierzone, Zapisz 3d: Dyskretnej wyewidencjonowanie  
 Ten test obejmuje podobszar scenariuszy gdzie **Wyewidencjonuj** okno dialogowe jest niewidoczny dla użytkownika **narzędzia**, **opcje**, **ustawienia kontroli źródła** .  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
- Po operacji wyewidencjonowania plików docelowych i/lub foldery są oznaczone jako wyewidencjonowane z magazynu wersji.  
  
- Magazyn wersji atrybuty wyewidencjonowanie do odpowiednich użytkowników.  
  
- Data i godzina wyewidencjonowanie jest poprawny (ustawienia dla każdego użytkownika).  
  
- Lokalna kopia pliku lub folderu docelowego jest zapisywalna.  
  
|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Dyskretnej wyewidencjonowania pliku|1.  Ustaw **narzędzia**, **opcje**, **kontroli źródła** do **wyewidencjonowanie plików automatycznie po edycji**.<br />2.  Utwórz nowy projekt z plikiem.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Zapoznaj się z pliku.|Plik jest wyewidencjonowany trybie dyskretnym (nie interfejsu użytkownika).|  
|Dyskretnej wyewidencjonowania projektu|1.  Ustaw **narzędzia**, **opcje**, **kontroli źródła** do **wyewidencjonowanie plików automatycznie po edycji**.<br />2.  Utwórz nowy projekt.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Zapoznaj się z projektu.|Plik jest wyewidencjonowany trybie dyskretnym (nie interfejsu użytkownika).|  
  
### <a name="case-3e-undo-check-out"></a>Wielkość 3e: Cofnij wyewidencjonowanie  
 **Cofnij wyewidencjonowanie** służy do anulowania plik wyewidencjonowany stanu i unikaj ewidencjonowania zmiany wprowadzone w pliku.  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
- Wartość domyślna jest podstawą użytkownika **zapoznaj się z lokalną wersją** ustawienie. Jeśli użytkownik wybierze zapoznaj się z lokalną wersją, wartość domyślna dla cofnięcie wyewidencjonowania jest zawsze wracają do wersji wyewidencjonowany.  
  
- Po zaakceptowaniu cofania, ikony w **Eksploratora rozwiązań** są aktualizowane, dla których to dotyczy plików, a element zostanie usunięty z **oczekujące elementy do zaewidencjonowania** okna.  
  
|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Cofnij wyewidencjonowanie pojedynczy plik, który został wyewidencjonowany w trybie wyłączności|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z plikiem wyłącznie.<br />4.  Zmodyfikuj plik.<br />5.  Cofnij wyewidencjonowanie (**pliku**, **kontroli źródła**, **Cofnij wyewidencjonowanie**).|Typowe oczekiwane zachowanie.|  
|Cofnij wyewidencjonowanie pojedynczy plik, który został wyewidencjonowany udostępnione|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z plikiem udostępnione.<br />4.  Zmodyfikuj plik.<br />5.  Cofnij wyewidencjonowanie (**pliku**, **kontroli źródła**, **Cofnij wyewidencjonowanie**).|Typowe oczekiwane zachowanie.|  
|Cofnij wyewidencjonowanie projektu po dodaniu plików do projektu|1.  Utwórz nowy projekt i dodaj go do kontroli źródła.<br />2.  Zapoznaj się z projektu.<br />3.  Dodaj plik do projektu.<br />4.  Cofnij wyewidencjonowanie projektu.|Dodany plik zostanie usunięty z projektu w Eksploratorze rozwiązań.<br /><br /> Projekt został już wyewidencjonowany.|  
|Cofnij wyewidencjonowanie projektu po usunięciu pliki z projektu|1.  Utwórz nowy projekt i dodaj go do kontroli źródła.<br />2.  Zapoznaj się z projektu.<br />3.  Usuń plik z projektu.<br />4.  Cofnij wyewidencjonowanie projektu.|Usunięto plik pojawia się w projekcie w Eksploratorze rozwiązań.<br /><br /> Projekt został już wyewidencjonowany.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
