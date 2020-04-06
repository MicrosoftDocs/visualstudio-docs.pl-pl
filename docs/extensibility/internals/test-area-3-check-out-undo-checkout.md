---
title: 'Obszar testowy 3: Sprawdź, czysz do odeszło do transakcji | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5365da1e342df5aea9c1b1cd2ae5a446baea57f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704618"
---
# <a name="test-area-3-check-outundo-checkout"></a>Obszar testu 3: Wyewidencjonuj/Cofnij wyewidencjonowanie
Ten obszar testu wtyczek kontroli źródła obejmuje edycję i przywracanie elementów z magazynu wersji za pomocą poleceń **Wyewidencjonuj** i **Cofnij wyewidencjonowanie.**

**Wyewidencjonuj**: Oznacza element w magazynie wersji jako wyewidencjonowany, modyfikuje lokalną kopię do odczytu/zapisu.

**Cofnij wyewidencjonowanie:** Oznacza element w magazynie wersji jako zaewidencjonowany, przywraca lokalną kopię do stanu przed wyewidencjonowywał (w zależności od opcji).

## <a name="command-menu-access"></a>Dostęp do menu polecenia

Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ścieżki menu zintegrowanego środowiska programistycznego są używane w przypadkach testowych.

##### <a name="check-out"></a>Wymelduj się:

- **Plik**, **Kontrola źródła**, **Wyewidencjonuj**.

- **Plik**, **Wyewidencjonuj**.

- Menu skrótów, **wyewidencjonuj**.

- Cofnij wyewidencjonowanie: **plik**, **kontrola źródła**, **Cofnij wyewidencjonowanie**.

## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie

- Po operacji wyewidencjonowania pliki docelowe i/lub foldery są oznaczone jako wyewidencjonowane w magazynie wersji.

- Magazyn wersji przypisuje wyewidencjonowanie do właściwego użytkownika.

- Godzina i data realizacji transakcji są poprawne (zgodnie z ustawieniami użytkownika).

## <a name="test-cases"></a>Przypadki testowe

Poniżej przedstawiono konkretne przypadki testowe dla obszaru testowego Wyewidencjonowanie/Cofnij wyewidencjonowanie.

### <a name="case-3a-check-out"></a>Przypadek 3a: Wyewidencjonuj

W tej sekcji skupiono się na działaniu polecenia wyewidencjonowywnika.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Wyewidencjonuj projekt klienta Exclusive (COE)|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Sprawdź cały projekt wyłącznie **(Plik,** **Check Out**).|Wyewidencjonuj występuje.|
|Wyewidencjonuj ekskluzywny (COE) system plików lub lokalny projekt sieci Web usług IIS|1. Ustaw połączenie serwera sieci Web na udostępnianie plików w **narzędziach,** **opcjach**, **projektach,** **ustawieniach sieci Web**.<br />2. Utwórz projekt sieci Web.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Sprawdź cały projekt wyłącznie **(Plik**, **Kontrola źródła,** **Check Out**).|Wyewidencjonuj występuje.|
|Wyewidencjonuj elementy rozwiązania w rozwiązaniu (nowa metoda obsługi innych plików)|1. Utwórz puste rozwiązanie.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Sprawdź rozwiązanie.<br />4. Dodaj kilka elementów rozwiązania.<br />5. Zamelduj się we wszystkich nowo dodanych elementach.<br />6. Wybierz wiele elementów rozwiązania.<br />7. Sprawdź wybrane elementy (Menu skrótów, **Wyewidencjonuj).**|Wybrane pliki są wyewidencjonowane.|
|Sprawdź wersję lokalną (jeśli w ramach testu wtyczka obsługuje tę funkcję)|1. Użytkownik 1: Utwórz projekt klienta.<br />2. Użytkownik 1: Dodaj rozwiązanie do kontroli źródła.<br />3. Użytkownik 2: Otwórz rozwiązanie z kontroli źródła do innej lokalizacji.<br />4. Użytkownik 2: Sprawdź plik.<br />5. Użytkownik 2: Zmodyfikuj plik.<br />6. Użytkownik 2: Zaewidencjonuj plik.<br />7. Użytkownik 1: Sprawdź lokalną wersję pliku (Sprawdź opcję Zaawansowana **wersja lokalna** w oknie dialogowym **Wyewidencjonowywanie).**|Lokalna wersja pliku jest wyewidencjonowana.<br /><br /> Modyfikacje wprowadzone przez użytkownika 2 nie są stosowane do pliku użytkownika 1.|

### <a name="case-3b-disconnected-check-out"></a>Przypadek 3b: Odłączony wyewidencjonowany

Praca w trybie odłączonym umożliwia użytkownikom pewien poziom ciągłej obsługi kontroli źródła, gdy nie jest podłączony bezpośrednio do magazynu wersji. Odbywa się to przez lokalnie buforowanie wszystkich istotnych informacji na temat edukanego rozwiązania i projektów.

Operacje wyewidencjonowania wyłącznego mogą wystąpić tylko po podłączeniu do magazynu kontroli źródła. Udostępnione operacje wyewidencjonowania mogą wystąpić w dowolnym momencie, niezależnie od tego, czy są połączone, czy rozłączone. W związku z tym po odłączeniu od magazynu wersji włączone jest tylko polecenie **Wyewidencjonuj udostępnione** (COS). Po rozłączeniu **cofnij wyewidencjonowanie** jest wyłączone, ponieważ nie można pobrać starej wersji w celu zastąpienia zmian wprowadzonych przez użytkownika.

Gdy użytkownik ponownie łączy się z magazynem wersji, stany wyewidencjonowania wszystkich powiązanych rozwiązań i projektów są synchronizowane. Spowoduje to wykonanie niezbędnych aktualizacji magazynu dla wyewidencjonowania, które użytkownik wykonał. Po zakończeniu synchronizacji użytkownik może kontynuować normalną pracę (połączoną).

#### <a name="expected-behavior"></a>Oczekiwane zachowanie

- Nie można użyć polecenia **Wyewidencjonuj wyłącznie** po odłączeniu od magazynu wersji.

- Nie można użyć polecenia **Cofnij wyewidencjonowanie** po odłączeniu od magazynu wersji.

- **Udostępnione polecenie Wyewidencjonuj** działa.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Po rozłączeniu wyewidencjonuj plik, a następnie połącz się w celu synchronizacji|1. Odłącz kontrolowany projekt za pomocą okna dialogowego Zmień formant źródła **(Plik,** **Kontrola źródła,** **Zmień kontrolę źródła).**<br />2. Wyewidencjonuj plik.<br />3. W oknie dialogowym z ostrzeżeniem kliknij pozycję Wyewidencjonuj (rozłączyno).<br />4. Edytuj plik.<br />5. Połącz połączenie za pomocą okna dialogowego Zmień formant źródła.<br />6. Pobierz najnowszą wersję edytowanego pliku.|Typowe oczekiwane zachowanie|

### <a name="case-3c-query-editquery-save-qeqs"></a>Przypadek 3c: Edycja kwerendy/Zapisywanie zapytań (QEQS)
 Elementy pod kontrolą źródła są śledzone pod kątem zmian, zmian i zapisów, aby ułatwić użytkownikom łatwe zarządzanie plikami. Gdy kontrolowany element, który jest "zaewidencjonowany" jest edytowany, QEQS przechwytuje próbę edycji i pyta użytkownika, czy chce wyewidencjonować plik, aby go edytować. W zależności od **narzędzia**, **Ustawienia opcji,** użytkownik jest zmuszony do wyewidencjonowania pliku w celu edycji lub może być może edytować kopię w pamięci i wyewidencjonować później. Jeśli użytkownik **Narzędzia**, **Opcje** ustawienie nie jest ustawiony, aby wyświetlić okno dialogowe wyewidencjonowywanie i po prostu sprawdzić, a następnie jako użytkownik sprawia, że jego edycji, plik automatycznie wyewidencjonowywane, gdy jest to możliwe.

#### <a name="expected-behavior"></a>Oczekiwane zachowanie

- Po operacji wyewidencjonowania pliki docelowe i/lub foldery są oznaczone jako wyewidencjonowane w magazynie wersji.

- Magazyn wersji przypisuje wyewidencjonowanie właściwemu użytkownikowi.

- Godzina i data wyewidencjonowania są poprawne (zgodnie z ustawieniami użytkownika).

- Można zapisać lokalną kopię pliku lub folderu docelowego.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Edytowanie zaewidencjonowanego pliku tekstowego|1. Utwórz nowy projekt zawierający plik tekstowy.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. **Ustawianie narzędzi,** **Opcje**, **Kontrola źródła**, **Zezwalaj na edytowanie plików, gdy pliki są tylko do odczytu na dysku,** aby nie były zaznaczone.<br />4. Ustaw **narzędzia**, **Opcje**, **Kontrola źródła**, Monit o **wyewidencjonowanie** **w polu po zaewidencjonowaniu plików są edytowane** pole kombi.<br />5. Ustaw **narzędzia**, **Opcje**, **Kontrola źródła**, Monit **o wyewidencjonowanie** **w polu po zaewidencjonowaniu plików są zapisywane** combo pole.<br />6. Otwórz plik tekstowy w edytorze, spróbuj wpisać nowy tekst do pliku. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />7. Kliknij **przycisk Anuluj** w oknie dialogowym **Wyewidencjonuj dla edycji.** Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />8. Ustaw **narzędzia**, **Opcje**, **Kontrola źródła**, **Zezwalaj na edycję plików podczas odczytu tylko na dysku,** aby sprawdzić.<br />9. Otwórz plik projektu w edytorze, spróbuj wpisać nowy tekst w pliku. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />10. Kliknij pozycję **Edytuj** w oknie dialogowym **Wyewidencjonuj dla edycji.** Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />11. Edytuj plik tekstowy i spróbuj go zapisać.|`Result of step 6:`<br /><br /> Wyświetl okno dialogowe Edycja.<br /><br /> `Result of step 7:`<br /><br /> Plik pozostaje niezmieniony.<br /><br /> `Result of step 9:`<br /><br /> Wyświetl okno dialogowe Edycja.<br /><br /> `Result of step 10:`<br /><br /> Plik projektu można edytować w pamięci.<br /><br /> `Result of step 11:`<br /><br /> Po zapisaniu zostanie wyświetlone okno dialogowe Wyewidencjonuj przy zapisywaniu.|
|Edytowanie zaewidencjonowanego pliku rozwiązania|Powtórz kroki opisane w poprzednim teście, ale zamiast modyfikować plik tekstowy, zmodyfikuj rozwiązanie, zmieniając właściwości rozwiązania.|Tak samo jak w poprzednim teście|
|Edytowanie zaewidencjonowanego pliku projektu|Powtórz kroki opisane w poprzednim teście, ale zamiast modyfikować plik tekstowy, zmodyfikuj projekt, zmieniając właściwości projektu.|Tak samo jak w poprzednim teście.|

### <a name="case-3d-silent-check-out"></a>Przypadek 3d: Cicha wymeldowanie
 Ten podobse jest omówiono scenariusze wyewidencjonowywanie, w których okno dialogowe **Wyewidencjonowywanie** nie jest wyświetlane dla **użytkownika — Narzędzia,** **Opcje**, Ustawienia **kontroli źródła**.

#### <a name="expected-behavior"></a>Oczekiwane zachowanie

- Po operacji wyewidencjonowania pliki docelowe i/lub foldery są oznaczone jako wyewidencjonowane w magazynie wersji.

- Magazyn wersji przypisuje wyewidencjonowanie właściwemu użytkownikowi.

- Godzina i data wyewidencjonowania jest poprawna (zgodnie z ustawieniami użytkownika).

- Można zapisać lokalną kopię pliku lub folderu docelowego.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Ciche wyewidencjonowanie pliku|1. Ustaw **narzędzia,** **Opcje,** **Kontrola źródła** do **automatycznego wyewidencjonowywać pliki podczas edycji**.<br />2. Utwórz nowy projekt z plikiem.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Sprawdź plik.|Plik jest wyewidencjonowany po cichu (bez interfejsu użytkownika).|
|Ciche wyewidencjonowanie projektu|1. Ustaw **narzędzia,** **Opcje,** **Kontrola źródła** do **automatycznego wyewidencjonowywać pliki podczas edycji**.<br />2. Utwórz nowy projekt.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Sprawdź projekt.|Plik jest wyewidencjonowany po cichu (bez interfejsu użytkownika).|

### <a name="case-3e-undo-check-out"></a>Przypadek 3e: Cofnij wyewidencjonowanie
 **Cofnij wyewidencjonowanie** służy do anulowania stanu wyewidencjonowanego pliku i uniknięcia zaewidencjonowania zmian wprowadzonych w pliku.

#### <a name="expected-behavior"></a>Oczekiwane zachowanie

- Wartość domyślna jest oparta na ustawieniu **Wyewidencjonuj wersję lokalną** użytkownika. Jeśli użytkownik wybrał wyewidencjonowanie wersji lokalnej, domyślnym ustawieniem wyewidencjonowania cofnąć jest zawsze powrót do wyewidencjonowanej wersji.

- Po zaakceptowaniu cofnięcia ikony w **Eksploratorze rozwiązań** są aktualizowane dla plików, których dotyczy problem, a element zostanie usunięty z okna **Oczekujące zaewidencjonowania.**

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Cofnij wyewidencjonowanie pojedynczego pliku, który jest wyewidencjonowany wyłącznie|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Sprawdź plik wyłącznie.<br />4. Zmodyfikuj plik.<br />5. Cofnij wyewidencjonowanie **(plik,** **kontrola źródła,** **Cofnij wyewidencjonowanie).**|Typowe oczekiwane zachowanie.|
|Cofanie wyewidencjonowywało pojedynczego pliku wyewidencjonowanego Udostępnionego|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Sprawdź udostępniony plik.<br />4. Zmodyfikuj plik.<br />5. Cofnij wyewidencjonowanie **(plik,** **kontrola źródła,** **Cofnij wyewidencjonowanie).**|Typowe oczekiwane zachowanie.|
|Cofanie wyewidencjonowywać projektu po dodaniu plików do projektu|1. Utwórz nowy projekt i dodaj go do kontroli źródła.<br />2. Sprawdź projekt.<br />3. Dodaj plik do projektu.<br />4. Cofnij kasę projektu.|Dodany plik zostanie usunięty z projektu w Eksploratorze rozwiązań.<br /><br /> Projekt nie jest już wyewidencjonowany.|
|Cofanie wyewidencjonowywania projektu po usunięciu plików z projektu|1. Utwórz nowy projekt i dodaj go do kontroli źródła.<br />2. Sprawdź projekt.<br />3. Usuń plik z projektu.<br />4. Cofnij kasę projektu.|Usunięty plik pojawia się w ramach projektu w Eksploratorze rozwiązań.<br /><br /> Projekt nie jest już wyewidencjonowany.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
