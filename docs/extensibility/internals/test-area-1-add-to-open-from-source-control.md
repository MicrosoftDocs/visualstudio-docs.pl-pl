---
title: 'Obszar testowy 1: Dodawanie do otwierania z kontroli źródła | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ba64bdcf299f52d0200e1fa66dead11a8824c14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429984"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Obszar testowy 1: Dodaj / Otwórz z kontroli źródła
Ta-wtyczka do kontroli źródła testów obszar obejmuje umieszczenie rozwiązań lub projektów pod kontrolą źródła i pobierania ich z kontroli źródła.

## <a name="command-menu-access"></a>Dostęp do Menu polecenia
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ścieżki menu środowiska zintegrowanego rozwoju są używane w przypadki testowe:

- Aby uzyskać [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], Otwórz z kontroli źródła: **Plik**, **Otwórz**, **projektu**/**rozwiązania**; Szukaj w [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] lokalizacji.

- Dla innych źródła wtyczek kontroli Otwórz z kontroli źródła: **Plik**, **kontroli źródła**, **Otwórz z kontroli źródła**.

- Dodaj do kontroli źródła: **Plik**, **kontroli źródła**, **Dodaj rozwiązanie do pliku kontroli źródła**, **kontroli źródła**, **Dodaj wybrane projekty do kontroli źródła**.

- Menu skrótów (projekt/rozwiązanie) **Dodaj rozwiązanie do kontroli źródła**.

- Dodaj z kontroli źródła: **Plik**, **kontroli źródła**, **Dodaj projekt z kontroli źródła**.

- Dla [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], Dodaj ze źródła kontrolki jest również dostępna z **pliku**, **Dodaj**, **istniejący projekt**; Szukaj w [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] lokalizacji.

  > [!NOTE]
  > Ścieżka pliku lokalnego lub lokalnych usług IIS (serwer sieci web) może służyć w tym teście.

## <a name="expected-behavior"></a>Oczekiwane zachowanie

- Dla każdego typu obsługiwanych projektu użytkownik powinien móc "Dodawanie do" i "Otwórz w" kontroli źródła.

- Gdy projekt jest dodawany do kontroli źródła, odpowiedni \< *ProjectName*> .vspscc (plik projektu wskazówka) jest tworzony. Zawiera on wykluczenia pliku listy oraz informacje o połączeniu. Nie usuwaj tego pliku, ponieważ zawiera on informacje specyficzne dla projektu.

- Po dodaniu rozwiązania do kontroli źródła, odpowiedni \< *SolutionName*> zostanie utworzony plik .vssscc (triple S). Plik tekstowy zawiera informacje o połączeniu i pliku listy wykluczeń, podobne do pliku podpowiedzi projektu. Ten plik jest tymczasowe i istnieje tylko w bazie danych kontroli źródła.

- Po otwarciu rozwiązania z kontroli źródła, \< *SolutionName*> plik .vsscc (podwójny S), który istnieje tylko w bazie danych kontroli źródła, jest tworzony lokalnie w pliku tymczasowym. Ten plik zawiera ścieżkę folderu połączenia rozwiązania do pliku rozwiązania. Ten plik jest tymczasowe i lokalna kopia jest usuwany po zakończeniu operacji "Otwórz z kontroli źródła".

- Po projekt jest dodawany do kontroli źródła, można wykonać akcje kontroli źródła na nim (wyewidencjonowania, Pobierz i tak dalej).

## <a name="test-cases"></a>Przypadki testowe
 Poniżej przedstawiono określonych przypadków testowych do dodawania / Otwórz z kontroli źródła obszar testowy.

### <a name="case-1a-add-solution-to-source-control"></a>Wielkość 1a: Dodaj rozwiązanie do kontroli źródła
 Ten przypadek testowy koncentruje się na dodawanie rozwiązania do kontroli źródła.

|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|
|------------|----------------|--------------------------------|
|Dodaj rozwiązania zawierającego projekt klienta do kontroli źródła|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj rozwiązanie do kontroli źródła**).|Rozwiązanie lub projekt docelowy został dodany do kontroli źródła.|
|Dodaj rozwiązanie, zawierający System plików lub lokalny projekt sieci Web usług IIS do kontroli źródła|1.  Tworzenie systemu plików lub lokalny projekt sieci Web usług IIS (Użyj przycisku Przeglądaj, aby wskazać lokalizację projektu; ścieżka Określa, jakiego typu Projekt sieci Web jest tworzony).<br />2.  Dodaj rozwiązanie do kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj rozwiązanie do kontroli źródła**).|Rozwiązanie lub projekt docelowy został dodany do kontroli źródła.|
|Dodaj rozwiązania zawierającego projekt zdalnej witryny sieci Web, do kontroli źródła|1.  Utwórz projekt zdalnej witryny sieci Web.<br />2.  Dodaj rozwiązanie do kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj rozwiązanie do kontroli źródła**).<br />3.  Kliknij przycisk **OK** dostępu FrontPage w oknie dialogowym ostrzeżenia.|Rozwiązanie zostało dodane do kontroli źródła.<br /><br /> Projekt witryny zdalnej nie jest pod kontrolą źródła. (Projekty lokacji zdalnej, muszą być kontrolowane z własnego serwera usług IIS).|
|Dodawanie rozwiązania do jednego projektu do kontroli źródła przy użyciu **Dodaj wybrane projekty do kontroli źródła**.|1.  Utwórz rozwiązanie pojedynczego projektu.<br />2.  Dodaj tylko rozwiązanie do kontroli źródła jako zaznaczenia (**pliku**, **kontroli źródła**, **Dodaj wybrane projekty do kontroli źródła**). Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />3.  Dodaj projekt do kontroli źródła jako wybór (**pliku**, **kontroli źródła**, **Dodaj wybrane projekty do kontroli źródła**).<br />4.  Kliknij przycisk **tak** można dodać projektu do tej samej lokalizacji.<br />5.  Kliknij przycisk **Wyewidencjonuj** w **Sprawdź się zmodyfikować** okno dialogowe.|`Result from Step 2:`<br /><br /> Projekt i wszystkie pliki w projekcie mają wyewidencjonowany się wskaźnik kontroli źródła i jest wyświetlana etykieta "nie pod kontrolą źródła".<br /><br /> `Result from Step 5:`<br /><br /> Pliki projektu i rozwiązania znajdują się w tym samym folderze, w kontroli źródła.|
|Anuluj dodawanie rozwiązania do kontroli źródła|1.  Utwórz rozwiązanie pojedynczego projektu.<br />2.  Próba dodania projektu i rozwiązania do kontroli źródła. Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />3.  Anuluj po znajdują się w systemie kontroli źródła.|`Result from Step 2:`<br /><br /> Tylko jeden raz pojawi się okno dialogowe kontroli źródła zestawu projektu lokalizacji.<br /><br /> `Result from Step 3:`<br /><br /> Projekt dodać anulowane, projekt/rozwiązanie nie jest pod kontrolą źródła, a wszystkie dodać do menu kontroli źródła jest nadal dostępna.|

### <a name="case-1b-open-solution-from-source-control"></a>1b wielkości liter. Otwórz rozwiązanie z kontroli źródła
 Ten przypadek testowy koncentruje się na otwarcie rozwiązania z kontroli źródła.

|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|
|------------|----------------|--------------------------------|
|Otwórz rozwiązanie zawierające projekt klienta z kontroli źródła|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Otwórz rozwiązanie z kontroli źródła do nowej lokalizacji.|Otwarte rozwiązanie lub projekt z kontroli źródła.|
|Otwórz rozwiązanie zawierające lokalnego lub projektu sieci Web usług IIS z kontroli źródła|1.  Tworzenie lokalnego lub projektu sieci Web usług IIS.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Otwórz rozwiązanie z kontroli źródła do nowej lokalizacji.|Otwarte rozwiązanie lub projekt z kontroli źródła.|
|Otwórz rozwiązanie zawierające projekt zdalnej witryny sieci Web z kontroli źródła|1.  Utwórz projekt zdalnej witryny sieci Web.<br />2.  Dodaj rozwiązanie do kontroli źródła. Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />3.  Zamknij rozwiązanie.<br />4.  Otwórz rozwiązanie z kontroli źródła do nowej lokalizacji.|`Result from Step 2:`<br /><br /> Zdalnej witryny sieci Web nie jest pod kontrolą źródła.<br /><br /> `Result from Step 4:`<br /><br /> Otworzyć rozwiązanie z kontroli źródła.<br /><br /> Projekt witryny zdalnej jest ładowany, ale nie jest pod kontrolą źródła.|

### <a name="case-1c-add-solution-from-source-control"></a>Przypadek 1c: Dodaj rozwiązanie z kontroli źródła
 Ten przypadek testowy koncentruje się na dodawanie rozwiązań z kontrolą źródła.

|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|
|------------|----------------|--------------------------------|
|Dodaj do rozwiązania pusty — rozwiązania pojedynczego projektu|1.  Utwórz rozwiązanie pojedynczego projektu.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Utwórz drugi puste rozwiązanie.<br />5.  Dodaj wcześniej kontrolowanego rozwiązanie z kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj projekt z kontroli źródła**).|Dodano projekt, który jest wyświetlany w **Eksploratora rozwiązań** i jest zaewidencjonowany.|
|Dodaj do rozwiązania przy użyciu pojedynczego projektu — pojedynczego projektu|1.  Tworzenie rozwiązań za pomocą pojedynczego projektu.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Utwórz drugi puste rozwiązanie.<br />5.  Dodaj wcześniej kontrolowanego rozwiązanie z kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj projekt z kontroli źródła**).|Dodano projekt, który jest wyświetlany w **Eksploratora rozwiązań** i jest zaewidencjonowany.|
|Dodaj do rozwiązania — rozwiązanie dodane do kontroli źródła według wyboru|1.  Tworzenie rozwiązania z projektem.<br />2.  Dodaj tylko rozwiązanie do kontroli źródła jako zaznaczenia. Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />3.  Zamknij rozwiązanie.<br />4.  Utwórz nowe rozwiązanie.<br />5.  Dodaj wcześniej kontrolowanego rozwiązanie z kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj projekt z kontroli źródła**).|`Result from Step 2:`<br /><br /> Projekt nie jest pod kontrolą źródła.<br /><br /> `Result from Step 5:`<br /><br /> Jeśli pierwsze rozwiązanie elementy rozwiązania, nie można ich dodać z poziomu kontroli źródła, więc nie są wyświetlane.<br /><br /> Projekt z pierwszego rozwiązania pojawia się jako niedostępny.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)