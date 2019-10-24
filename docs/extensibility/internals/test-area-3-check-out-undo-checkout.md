---
title: 'Obszar testowy 3: wyewidencjonowywanie — cofanie wyewidencjonowania | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44abff5adedf8e0cccfb0d5e44486aaa8f36ff12
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722561"
---
# <a name="test-area-3-check-outundo-checkout"></a>Obszar testowy 3: wyewidencjonowywanie/cofanie wyewidencjonowania
Ten obszar testowy wtyczki kontroli źródła obejmuje edytowanie i wycofywanie elementów z magazynu wersji za pomocą poleceń **wyewidencjonowywania** i **cofania wyewidencjonowania** .

**Wyewidencjonowywanie**: oznacza element w sklepie wersji jako wyewidencjonowany, modyfikuje kopię lokalną na odczyt/zapis.

**Cofnij wyewidencjonowanie**: oznacza element w sklepie wersji jako zaewidencjonowany, przywraca lokalne kopiowanie do stanu przed wyewidencjonowaniem (w zależności od opcji).

## <a name="command-menu-access"></a>Dostęp do menu poleceń

W przypadku przypadków testowych używane są [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] następujące ścieżki menu zintegrowanego środowiska deweloperskiego.

##### <a name="check-out"></a>Wymelduj się:

- **Plik**, **Kontrola źródła**, **wyewidencjonowywanie**.

- **Plik**, **Wyewidencjonuj**.

- Menu skrótów, **Wyewidencjonuj**.

- Cofnij wyewidencjonowanie: **plik**, **Kontrola źródła**, **Cofnij wyewidencjonowanie**.

## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie

- Po zakończeniu operacji wyewidencjonowywania pliki i/lub foldery docelowe są oznaczane jako wyewidencjonowane w sklepie z wersjami.

- Magazyn wersji ma atrybuty wyewidencjonowania dla poprawnego użytkownika.

- Godzina i Data wyewidencjonowania są poprawne (zgodnie z ustawieniami użytkownika).

## <a name="test-cases"></a>Przypadki testowe

Poniżej wymieniono określone przypadki testowe dla obszaru testowego wyewidencjonowywania/cofania wyewidencjonowania.

### <a name="case-3a-check-out"></a>Przypadek 3A: wyewidencjonowywanie

Ta sekcja koncentruje się na operacji wyewidencjonowania polecenia.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Wyewidencjonowywanie wyłącznego (COE) projektu klienta|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Sprawdź cały projekt (**plik**, **Wyewidencjonuj**).|Wyewidencjonowanie.|
|Wyewidencjonowywanie wyłącznego (COE) systemu plików lub lokalnego projektu sieci Web usług IIS|1. Skonfiguruj połączenie serwera sieci Web z udziałem plików w **Narzędzia**, **Opcje**, **projekty**, **Ustawienia sieci Web**.<br />2. Utwórz projekt sieci Web.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Sprawdź cały projekt wyłącznie (**plik**, **Kontrola źródła**, **wyewidencjonowywanie**).|Wyewidencjonowanie.|
|Sprawdź elementy rozwiązania w rozwiązaniu (Nowa metoda obsługi innych plików)|1. Utwórz puste rozwiązanie.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Sprawdź rozwiązanie.<br />4. Dodaj kilka elementów rozwiązania.<br />5. Zaewidencjonuj wszystkie nowo dodane elementy.<br />6. Wybierz wiele elementów rozwiązania.<br />7. Sprawdź wybrane elementy (menu skrótów, **Wyewidencjonuj**).|Wybrane pliki są wyewidencjonowane.|
|Wyewidencjonuj lokalną wersję (jeśli wtyczka w teście obsługuje tę funkcję)|1. Użytkownik 1: Tworzenie projektu klienta.<br />2. Użytkownik 1: Dodaj rozwiązanie do kontroli źródła.<br />3. Użytkownik 2: Otwórz rozwiązanie z kontroli źródła w innej lokalizacji.<br />4. Użytkownik 2: Wyewidencjonuj plik.<br />5. Użytkownik 2: Modyfikuj plik.<br />6. Użytkownik 2: Zaewidencjonuj plik.<br />7. Użytkownik 1: wyewidencjonowywanie lokalnej wersji pliku (zaznacz opcję Wyewidencjonuj **lokalną wersję** zaawansowaną w oknie dialogowym **wyewidencjonowywanie** ).|Lokalna wersja pliku została wyewidencjonowana.<br /><br /> Modyfikacje wprowadzone przez użytkownika 2 nie są stosowane do pliku User 1.|

### <a name="case-3b-disconnected-check-out"></a>Przypadek 3B: odłączono wyewidencjonowanie

Działanie w trybie rozłączonym umożliwia użytkownikom pewien poziom wsparcia kontroli źródła, gdy nie jest on dołączony bezpośrednio do sklepu z wersjami. Jest to realizowane przez lokalne buforowanie wszystkich istotnych informacji o zarejestrowanym rozwiązaniu i projektach.

Operacje wyewidencjonowania wyłącznego mogą wystąpić tylko podczas połączenia z magazynem kontroli źródła. Udostępnione operacje wyewidencjonowania mogą wystąpić w dowolnym momencie, niezależnie od tego, czy jest połączony czy odłączony. W związku z tym po rozłączeniu z magazynem wersji jest włączone tylko polecenie **wyewidencjonowanie udostępnione** (cos). Po rozłączeniu polecenie **Cofnij wyewidencjonowanie** jest wyłączone, ponieważ nie można pobrać starej wersji, aby zastąpić zmiany wprowadzone przez użytkownika.

Gdy użytkownik ponownie nawiązuje połączenie z magazynem wersji, synchronizowane są Stany wyewidencjonowania wszystkich zarejestrowanych rozwiązań i projektów. W ten sposób są wymagane aktualizacje magazynu dla wyewidencjonowania wykonywanego przez użytkownika. Po zakończeniu synchronizacji użytkownik może kontynuować pracę jako normalną (połączona).

#### <a name="expected-behavior"></a>Oczekiwane zachowanie

- Nie można użyć polecenia **wyewidencjonowywania wyłącznie** w trakcie rozłączenia z magazynem wersji.

- Nie można użyć polecenia **Cofnij wyewidencjonowania** w trakcie rozłączenia z magazynem wersji.

- **Udostępnione polecenie wyewidencjonowania** działa.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Po rozłączeniu Wyewidencjonuj plik, a następnie połącz się z synchronizacją|1. Odłącz kontrolowany projekt przy użyciu okna dialogowego Zmień kontrolę źródła (**plik**, **Kontrola źródła**, **zmiana kontroli źródła**).<br />2. Sprawdź plik.<br />3. kliknij pozycję Wyewidencjonuj (Rozłączono) w oknie dialogowym ostrzeżenia.<br />4. Edytuj plik.<br />5. Połącz się przy użyciu okna dialogowego Zmień kontrolę źródła.<br />6. Pobierz najnowszą wersję edytowanego pliku.|Typowe oczekiwane zachowanie|

### <a name="case-3c-query-editquery-save-qeqs"></a>Przypadek 3C: modyfikowanie zapytania/zapisywanie zapytania (QEQS)
 Elementy pod kontrolą źródła są śledzone pod kątem zmian, zmian i zapisywanych danych, aby ułatwić użytkownikom zarządzanie swoimi plikami. Gdy kontrolowany element, który jest "zaewidencjonowany" jest edytowany, QEQS przechwytuje próbną edycję i pyta użytkownika, czy chce wyewidencjonować plik, aby go edytować. W zależności od **narzędzi**, ustawień **opcji** , użytkownik jest zmuszony do wyewidencjonowania pliku, aby można było go edytować lub może edytować kopię w pamięci i wypróbować go później. Jeśli **Narzędzia**użytkownika, ustawienie **opcji** nie jest ustawione na wyświetlanie okna dialogowego Wyewidencjonowywanie i po prostu Wyewidencjonuj, a następnie użytkownik dokona edycji, plik zostanie automatycznie wyewidencjonowany, jeśli jest to możliwe.

#### <a name="expected-behavior"></a>Oczekiwane zachowanie

- Po zakończeniu operacji wyewidencjonowywania pliki i/lub foldery docelowe są oznaczane jako wyewidencjonowane w sklepie z wersjami.

- Magazyn wersji ma atrybuty wyewidencjonowania dla poprawnego użytkownika.

- Godzina i Data wyewidencjonowania są poprawne (zgodnie z ustawieniami użytkownika).

- Lokalna kopia docelowego pliku lub folderu jest zapisywalna.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Edytuj plik tekstowy, który jest zaewidencjonowany|1. Utwórz nowy projekt zawierający plik tekstowy.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Ustaw **Narzędzia**, **Opcje**, **Kontrola źródła**, **Zezwól na edycję plików, gdy tylko do odczytu na dysku mają być** niezaznaczone.<br />4. Ustaw **Narzędzia**, **Opcje**, **Kontrola źródła**i **Monituj o** wyewidencjonowanie w polu kombi, **gdy zaewidencjonowano pliki są edytowane** .<br />5. Ustaw **Narzędzia**, **Opcje**, **Kontrola źródła**i **Monituj o** wyewidencjonowanie w polu kombi **gdy zaznaczone pliki są zapisywane** .<br />6. Otwórz plik tekstowy w edytorze, a następnie spróbuj wpisać nowy tekst do pliku. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />7. kliknij przycisk **Anuluj** w oknie dialogowym **wyewidencjonowywanie dla edycji** . Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />8. Ustaw **Narzędzia**, **Opcje**, **Kontrola źródła**, **Zezwól na edycję plików, gdy tylko do odczytu na dysku zostaną** zaznaczone.<br />9. Otwórz plik projektu w edytorze, a następnie spróbuj wpisać nowy tekst w pliku. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />10. kliknij przycisk **Edytuj** w oknie dialogowym **wyewidencjonowywanie dla edycji** . Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />11. Edytuj plik tekstowy i spróbuj go zapisać.|`Result of step 6:`<br /><br /> Zostanie wyświetlone okno dialogowe Wyewidencjonuj do edycji.<br /><br /> `Result of step 7:`<br /><br /> Plik jest niezmieniony.<br /><br /> `Result of step 9:`<br /><br /> Zostanie wyświetlone okno dialogowe Wyewidencjonuj do edycji.<br /><br /> `Result of step 10:`<br /><br /> Plik projektu można edytować w pamięci.<br /><br /> `Result of step 11:`<br /><br /> Przy zapisywaniu zostanie wyświetlone okno dialogowe wyewidencjonowywanie przy zapisywaniu.|
|Edytuj plik rozwiązania, który jest zaewidencjonowany|Powtórz kroki zgodnie z opisem w poprzednim teście, ale zamiast modyfikować plik tekstowy, zmodyfikuj rozwiązanie, zmieniając właściwości rozwiązania.|Taki sam jak poprzedni test|
|Edytuj plik projektu, który jest zaewidencjonowany|Powtórz kroki zgodnie z opisem w poprzednim teście, ale zamiast modyfikować plik tekstowy, zmodyfikuj projekt, zmieniając właściwości projektu.|Taki sam jak poprzedni test.|

### <a name="case-3d-silent-check-out"></a>Przypadek 3W: ciche wyewidencjonowywanie
 Ten obszar podrzędny obejmuje sprawdzenie scenariuszy, w których okno dialogowe **wyewidencjonowywania** nie pojawia się na poszczególnych użytkownikach **,** **opcjach**, **ustawieniach kontroli źródła**.

#### <a name="expected-behavior"></a>Oczekiwane zachowanie

- Po zakończeniu operacji wyewidencjonowywania pliki i/lub foldery docelowe są oznaczane jako wyewidencjonowane w sklepie z wersjami.

- Magazyn wersji ma atrybuty wyewidencjonowania dla poprawnego użytkownika.

- Godzina i Data wyewidencjonowania są poprawne (zgodnie z ustawieniami użytkownika).

- Lokalna kopia docelowego pliku lub folderu jest zapisywalna.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Wyewidencjonowywanie dyskretne pliku|1. Ustaw **Narzędzia**, **Opcje**, **Kontrola źródła** w celu **automatycznego wyewidencjonowania plików podczas edycji**.<br />2. Utwórz nowy projekt z plikiem.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Wyewidencjonuj plik.|Plik został wyewidencjonowany w trybie dyskretnym (brak interfejsu użytkownika).|
|Wyewidencjonowywanie dyskretne dla projektu|1. Ustaw **Narzędzia**, **Opcje**, **Kontrola źródła** w celu **automatycznego wyewidencjonowania plików podczas edycji**.<br />2. Utwórz nowy projekt.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Sprawdź projekt.|Plik został wyewidencjonowany w trybie dyskretnym (brak interfejsu użytkownika).|

### <a name="case-3e-undo-check-out"></a>Przypadek 3e: Cofnij wyewidencjonowanie
 **Cofnięcie** wyewidencjonowania służy do anulowania stanu wyewidencjonowania pliku i unikania zaewidencjonowania zmian wprowadzonych w pliku.

#### <a name="expected-behavior"></a>Oczekiwane zachowanie

- Wartość domyślna jest określana na podstawie ustawienia **wersja lokalna wyewidencjonowania** użytkownika. Jeśli użytkownik wybrał opcję wyewidencjonowania lokalnej wersji, wartość domyślna dla opcji Cofnij wyewidencjonowanie ma zawsze na celu przywrócenie wersji wyewidencjonowanej.

- Po zaakceptowaniu operacji cofania ikony w **Eksplorator rozwiązań** są aktualizowane dla plików, których dotyczy, a element zostanie usunięty z okna **Oczekujące zaewidencjonowania** .

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Cofnij wyewidencjonowanie pojedynczego pliku, który jest wyewidencjonowany na wyłączność|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Wyewidencjonuj plik w trybie wyłączności.<br />4. Zmodyfikuj plik.<br />5. Cofnij wyewidencjonowanie (**plik**, **Kontrola źródła**, **Cofnij wyewidencjonowanie**).|Typowe oczekiwane zachowanie.|
|Cofnij wyewidencjonowanie pojedynczego pliku, który został wyewidencjonowany jako udostępniony|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Zapoznaj się z udostępnionym plikiem.<br />4. Zmodyfikuj plik.<br />5. Cofnij wyewidencjonowanie (**plik**, **Kontrola źródła**, **Cofnij wyewidencjonowanie**).|Typowe oczekiwane zachowanie.|
|Cofnij wyewidencjonowanie projektu po dodaniu plików do projektu|1. Utwórz nowy projekt i dodaj go do kontroli źródła.<br />2. Sprawdź projekt.<br />3. Dodaj plik do projektu.<br />4. Cofnij wyewidencjonowanie projektu.|Dodany plik zostanie usunięty z projektu w Eksplorator rozwiązań.<br /><br /> Projekt nie jest już wyewidencjonowany.|
|Cofnij wyewidencjonowanie projektu po usunięciu plików z projektu|1. Utwórz nowy projekt i dodaj go do kontroli źródła.<br />2. Sprawdź projekt.<br />3. Usuń plik z projektu.<br />4. Cofnij wyewidencjonowanie projektu.|Usunięty plik jest wyświetlany w obszarze projektu w Eksplorator rozwiązań.<br /><br /> Projekt nie jest już wyewidencjonowany.|

## <a name="see-also"></a>Zobacz także
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
