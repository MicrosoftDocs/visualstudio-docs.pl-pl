---
title: 'Obszar badania 1: Dodaj do otwarcia z kontroli źródła | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ac7b8e5a60fe25ac22272cc28fc3ed6f903b058
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704680"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Obszar testowy 1: Dodaj/Otwórz z kontroli źródła
Ten obszar testu wtyczki kontroli źródła obejmuje umieszczanie rozwiązań lub projektów pod kontrolą źródła i pobieranie ich z kontroli źródła.

## <a name="command-menu-access"></a>Dostęp do menu polecenia
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ścieżki menu zintegrowanego środowiska programistycznego są używane w przypadkach testowych:

- Dla [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], open from source control: **Plik**, **Otwórz**,**Rozwiązanie** **projektu**/; w [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] lokalizacji.

- W przypadku innych wtyczek kontroli źródła otwórz z kontroli źródła: **Plik**, **Kontrola źródła,** **Otwórz z kontroli źródła**.

- Dodaj do formantu źródła: **Plik**, **Kontrola źródła**, **Dodaj rozwiązanie do pliku kontroli źródła**, **Formant źródła**, Dodaj wybrane projekty do kontroli **źródła**.

- Menu skrótów (projekt/rozwiązanie), **dodaj rozwiązanie do kontroli źródła**.

- Dodaj z formantu źródła: **Plik**, **Kontrola źródła**, **Dodaj projekt z kontroli źródła**.

- For [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], add from source control is also available from File , Add , Existing Project ; For , add from source control is also available from File , Add , Existing Project ; For , add from source control is also available from **File**, **Add**, **Existing Project**; w [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] lokalizacji.

  > [!NOTE]
  > W tym teście można użyć ścieżki pliku lokalnego lub lokalnego serwera sieci Web (IIS).

## <a name="expected-behavior"></a>Oczekiwane zachowanie

- Dla każdego obsługiwanego typu projektu użytkownik powinien mieć możliwość "Dodaj do" i "Otwórz z" Kontroli źródła.

- Po dodaniu projektu do kontroli \<źródła tworzony jest odpowiedni plik *projectname*>.vspscc (plik podpowiedzi projektu). Zawiera listę plików wykluczeń i informacje o połączeniu. Nie należy usuwać tego pliku, ponieważ zawiera on informacje specyficzne dla projektu.

- Po dodaniu rozwiązania do kontroli \<źródła tworzony jest odpowiedni plik>.vssscc (triple S). *SolutionName* Plik tekstowy zawiera informacje o połączeniu i listę plików wykluczeń, podobnie jak plik wskazówki projektu. Ten plik jest tymczasowy i istnieje tylko w bazie danych kontroli źródła.

- Gdy rozwiązanie jest otwierane z \<kontroli źródła, *plik SolutionName*>.vsscc (double S), który istnieje tylko w bazie danych kontroli źródła, jest tworzony lokalnie w pliku tymczasowym. Ten plik zawiera ścieżkę z folderu połączenia rozwiązania do pliku rozwiązania. Ten plik jest tymczasowy, a kopia lokalna jest usuwana po zakończeniu operacji "Otwórz z kontroli źródła".

- Po dodaniu projektu do formantu źródła można wykonać dowolną akcjonasowanie kontroli źródła (Wyewidencjonuj, Pobierz i tak dalej).

## <a name="test-cases"></a>Przypadki testowe
 Poniżej przedstawiono konkretne przypadki testowe dla obszaru testowego Dodaj do/otwórz z źródła kontroli.

### <a name="case-1a-add-solution-to-source-control"></a>Przypadek 1a: Dodaj rozwiązanie do kontroli źródła
 Ten przypadek testowy koncentruje się na dodawaniu rozwiązań do kontroli źródła.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Dodawanie rozwiązania zawierającego projekt klienta do kontroli źródła|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła **(Plik**, **Kontrola źródła,** **Dodaj rozwiązanie do kontroli źródła).**|Rozwiązanie/projekt został dodany do kontroli źródła.|
|Dodawanie rozwiązania zawierającego system plików lub lokalny projekt sieci Web usług IIS do kontroli źródła|1. Utwórz system plików lub lokalny projekt sieci Web usług IIS (użyj przycisku Przeglądaj, aby wskazać lokalizację projektu; ścieżka określa, jaki typ projektu sieci Web jest tworzony).<br />2. Dodaj rozwiązanie do kontroli źródła **(Plik**, **Kontrola źródła,** **Dodaj rozwiązanie do kontroli źródła).**|Rozwiązanie/projekt został dodany do kontroli źródła.|
|Dodawanie rozwiązania zawierającego projekt witryny zdalnej w sieci Web do kontroli źródła|1. Utwórz projekt witryny zdalnej w sieci Web.<br />2. Dodaj rozwiązanie do kontroli źródła **(Plik**, **Kontrola źródła,** **Dodaj rozwiązanie do kontroli źródła).**<br />3. Kliknij **przycisk OK** w oknie dialogowym z ostrzeżeniem programu Access programu FrontPage.|Rozwiązanie zostało dodane do kontroli źródła.<br /><br /> Projekt lokacji zdalnej NIE jest pod kontrolą źródła. (Projekty lokacji zdalnej muszą być kontrolowane z własnego serwera usług IIS).|
|Dodaj jedno rozwiązanie projektu do kontroli źródła przy użyciu **opcji Dodaj wybrane projekty do kontroli źródła**.|1. Utwórz rozwiązanie pojedynczego projektu.<br />2. Dodaj tylko rozwiązanie do kontroli źródła jako zaznaczenie **(Plik**, **Kontrola źródła,** **Dodaj wybrane projekty do kontroli źródła).** Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />3. Dodaj projekt do kontroli źródła jako wybór **(Plik**, **Kontrola źródła,** **Dodaj wybrane projekty do kontroli źródła).**<br />4. Kliknij **przycisk Tak,** aby dodać projekt do tej samej lokalizacji.<br />5. Kliknij pozycję **Wyewidencjonuj** w oknie dialogowym **Wyewidencjonuj do edycji.**|`Result from Step 2:`<br /><br /> Projekt i wszystkie pliki w ramach projektu mają wyewidencjonowany wskaźnik kontroli źródła, a etykietka narzędzia wyświetla "Nie pod kontrolą źródła".<br /><br /> `Result from Step 5:`<br /><br /> Plik projektu i rozwiązania znajdują się w tym samym folderze w kontroli źródła.|
|Anulowanie dodawania rozwiązania do formantu źródła|1. Utwórz rozwiązanie pojedynczego projektu.<br />2. Spróbuj dodać projekt i rozwiązanie do kontroli źródła. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />3. Anuluj po tym, jak jesteś w systemie kontroli źródła.|`Result from Step 2:`<br /><br /> Okno dialogowe Ustawianie źródła lokalizacji projektu jest wyświetlane tylko raz.<br /><br /> `Result from Step 3:`<br /><br /> Projekt dodać anulowane, projekt/rozwiązanie nie jest pod kontrolą źródła i wszystkie Dodaj do menu kontroli źródła nadal dostępne.|

### <a name="case-1b-open-solution-from-source-control"></a>Sprawa 1b. Otwórz rozwiązanie z kontroli źródła
 Ten przypadek testowy koncentruje się na otwieraniu rozwiązań z kontroli źródła.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Otwieranie rozwiązania zawierającego projekt klienta z kontroli źródła|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Zamknąć roztwór.<br />4. Otwórz rozwiązanie z kontroli źródła do nowej lokalizacji.|Rozwiązanie/projekt otwarty z kontroli źródła.|
|Otwieranie rozwiązania zawierającego lokalny lub iis webowy projekt z formantu źródłowego|1. Utwórz projekt lokalny lub IIS Web.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Zamknąć roztwór.<br />4. Otwórz rozwiązanie z kontroli źródła do nowej lokalizacji.|Rozwiązanie/projekt otwarty z kontroli źródła.|
|Otwieranie rozwiązania zawierającego projekt witryny zdalnej w sieci Web z formantu źródłowego|1. Utwórz projekt witryny zdalnej w sieci Web.<br />2. Dodaj rozwiązanie do kontroli źródła. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />3. Zamknąć roztwór.<br />4. Otwórz rozwiązanie z kontroli źródła do nowej lokalizacji.|`Result from Step 2:`<br /><br /> Witryna zdalna w sieci Web NIE jest pod kontrolą źródła.<br /><br /> `Result from Step 4:`<br /><br /> Rozwiązanie otwarte z kontroli źródła.<br /><br /> Projekt lokacji zdalnej jest ładowany, ale nie jest pod kontrolą źródła.|

### <a name="case-1c-add-solution-from-source-control"></a>Przypadek 1c: Dodaj rozwiązanie z kontroli źródła
 Ten przypadek testowy koncentruje się na dodawaniu rozwiązań z kontroli źródła.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Dodaj do pustego rozwiązania — rozwiązanie pojedynczego projektu|1. Utwórz rozwiązanie pojedynczego projektu.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Zamknąć roztwór.<br />4. Utwórz drugie puste rozwiązanie.<br />5. Dodaj wcześniej kontrolowane rozwiązanie z kontroli źródła **(File**, **Source Control**, Add Project from **Source Control).**|Dodany projekt pojawi się w **Eksploratorze rozwiązań** i jest zaewidencjonowany.|
|Dodaj do rozwiązania za pomocą pojedynczego projektu — pojedynczy projekt|1. Utwórz rozwiązanie z jednym projektem.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Zamknąć roztwór.<br />4. Utwórz drugie puste rozwiązanie.<br />5. Dodaj wcześniej kontrolowane rozwiązanie z kontroli źródła **(File**, **Source Control**, Add Project from **Source Control).**|Dodany projekt pojawi się w **Eksploratorze rozwiązań** i jest zaewidencjonowany.|
|Dodaj do rozwiązania — rozwiązanie dodane do kontroli źródła przez wybór|1. Tworzenie rozwiązania z projektem.<br />2. Dodaj tylko rozwiązanie do kontroli źródła jako wybór. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />3. Zamknąć roztwór.<br />4. Stwórz nowe rozwiązanie.<br />5. Dodaj wcześniej kontrolowane rozwiązanie z kontroli źródła **(File**, **Source Control**, Add Project from **Source Control).**|`Result from Step 2:`<br /><br /> Projekt nie jest pod kontrolą źródła.<br /><br /> `Result from Step 5:`<br /><br /> Jeśli pierwsze rozwiązanie miało elementy rozwiązania, nie można ich dodać z kontroli źródła, więc nie są wyświetlane.<br /><br /> Projekt z pierwszego rozwiązania jest wyświetlany jako niedostępny.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
