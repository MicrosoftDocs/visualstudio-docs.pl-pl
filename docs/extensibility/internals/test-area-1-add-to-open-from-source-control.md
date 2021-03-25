---
title: 'Obszar testowy 1: Dodawanie To-Open z kontroli źródła | Microsoft Docs'
description: Ten obszar testowania wtyczki kontroli źródła obejmuje umieszczanie rozwiązań lub projektów pod kontrolą źródła oraz pobieranie ich z kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 174834dde4c049bcb1b3fd8bc2eb8e82166d01d4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078698"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Obszar testowy 1: dodawanie do kontroli kodu źródłowego i otwieranie z poziomu kontroli kodu źródłowego
Ten obszar testowania wtyczki kontroli źródła obejmuje umieszczanie rozwiązań lub projektów pod kontrolą źródła oraz pobieranie ich z kontroli źródła.

## <a name="command-menu-access"></a>Dostęp do menu poleceń
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ścieżki menu zintegrowanego środowiska deweloperskiego są używane w przypadkach testowych:

- W przypadku programu [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Otwórz z kontroli źródła: **plik**, **otwarte**,  / **rozwiązanie** projektu; Znajdź [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] lokalizację.

- W przypadku innych wtyczek kontroli źródła otwórz z kontroli źródła: **plik**, **Kontrola źródła**, **Otwórz z kontroli źródła**.

- Dodaj do kontroli źródła: **plik**, **Kontrola źródła**, **Dodaj rozwiązanie do pliku kontroli źródła**, **kontroli źródła**, **Dodaj wybrane projekty do kontroli źródła**.

- Menu skrótów (projekt/rozwiązanie), **Dodaj rozwiązanie do kontroli źródła**.

- Dodaj z kontroli źródła: **plik**, **Kontrola źródła**, **Dodaj projekt z kontroli źródła**.

- Dla programu [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] , Dodaj z kontroli źródła jest również dostępna z **pliku**, **Dodaj**, **istniejący projekt**. Poszukaj w [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] lokalizacji.

  > [!NOTE]
  > W tym teście można użyć ścieżki lokalnego pliku lub lokalnych usług IIS (serwer sieci Web).

## <a name="expected-behavior"></a>Oczekiwane zachowanie

- Dla każdego obsługiwanego typu projektu użytkownik powinien mieć możliwość "Dodaj do" i "Otwórz z" kontroli źródła.

- Po dodaniu projektu do kontroli źródła \<*ProjectName*> jest tworzony odpowiedni plik. VSPSCC (plik podpowiedzi projektu). Zawiera listę plików wykluczeń i informacje o połączeniu. Nie usuwaj tego pliku, ponieważ zawiera on informacje specyficzne dla projektu.

- Po dodaniu rozwiązania do kontroli źródła \<*SolutionName*> zostanie utworzony odpowiedni plik. VSSSCC (potrójny). Plik tekstowy zawiera informacje o połączeniu i listę plików wykluczeń, podobnie jak w przypadku pliku podpowiedzi projektu. Ten plik jest tymczasowy i istnieje tylko w bazie danych kontroli źródła.

- Gdy rozwiązanie jest otwierane z kontroli źródła, \<*SolutionName*> plik. vsscc (Double S), który istnieje tylko w bazie danych kontroli źródła, jest tworzony lokalnie w pliku tymczasowym. Ten plik zawiera ścieżkę z folderu połączenia rozwiązania do pliku rozwiązania. Ten plik jest tymczasowy, a kopia lokalna jest usuwana po zakończeniu operacji "Otwórz z kontroli źródła".

- Po dodaniu projektu do kontroli źródła można wykonać na nim wszystkie akcje kontroli źródła (wyewidencjonowania, get itd.).

## <a name="test-cases"></a>Przypadki testowe
 Poniżej wymieniono określone przypadki testowe dla obszaru testowego Dodaj/Otwórz z kontroli źródła.

### <a name="case-1a-add-solution-to-source-control"></a>Przypadek 1a: Dodawanie rozwiązania do kontroli źródła
 Ten przypadek testowy koncentruje się na dodawaniu rozwiązań do kontroli źródła.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Dodaj rozwiązanie zawierające projekt klienta do kontroli źródła|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła (**plik**, **Kontrola źródła**, **Dodaj rozwiązanie do kontroli źródła**).|Rozwiązanie/projekt zostało dodane do kontroli źródła.|
|Dodaj rozwiązanie zawierające system plików lub lokalny projekt sieci Web usług IIS do kontroli źródła|1. Utwórz system plików lub lokalny projekt sieci Web usług IIS (Użyj przycisku Przeglądaj, aby wskazać lokalizację projektu; ścieżka Określa, jaki typ projektu sieci Web jest tworzony).<br />2. Dodaj rozwiązanie do kontroli źródła (**plik**, **Kontrola źródła**, **Dodaj rozwiązanie do kontroli źródła**).|Rozwiązanie/projekt zostało dodane do kontroli źródła.|
|Dodaj rozwiązanie zawierające projekt sieci Web zdalnej witryny do kontroli źródła|1. Utwórz projekt sieci Web zdalnej witryny.<br />2. Dodaj rozwiązanie do kontroli źródła (**plik**, **Kontrola źródła**, **Dodaj rozwiązanie do kontroli źródła**).<br />3. kliknij przycisk **OK** w oknie dialogowym ostrzeżenia dostępu do programu FrontPage.|Dodano rozwiązanie do kontroli źródła.<br /><br /> Projekt witryny zdalnej nie znajduje się pod kontrolą źródła. (Projekty lokacji zdalnych muszą być kontrolowane przez swój własny serwer IIS).|
|Dodaj jedno rozwiązanie projektu do kontroli źródła przy użyciu polecenia **Dodaj wybrane projekty do kontroli źródła**.|1. Utwórz rozwiązanie pojedynczego projektu.<br />2. Dodaj tylko rozwiązanie do kontroli źródła jako zaznaczenie (**plik**, **Kontrola źródła**, **Dodaj wybrane projekty do kontroli źródła**). Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />3. Dodaj projekt do kontroli źródła jako zaznaczenie (**plik**, **Kontrola źródła**, **Dodaj wybrane projekty do kontroli źródła**).<br />4. kliknij przycisk **tak** , aby dodać projekt do tej samej lokalizacji.<br />5. kliknij pozycję **Wyewidencjonuj** , **Aby edytować** okno dialogowe.|`Result from Step 2:`<br /><br /> Projekt i wszystkie pliki w projekcie mają sprawdzony wskaźnik kontroli źródła, a etykietka narzędzia wyświetla "nie pod kontrolą źródła".<br /><br /> `Result from Step 5:`<br /><br /> Plik projektu i rozwiązania znajdują się w tym samym folderze w kontroli źródła.|
|Anuluj Dodawanie rozwiązania do kontroli źródła|1. Utwórz rozwiązanie pojedynczego projektu.<br />2. Spróbuj dodać projekt i rozwiązanie do kontroli źródła. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />3. Anuluj po przejściu w system kontroli źródła.|`Result from Step 2:`<br /><br /> Okno dialogowe Ustawianie kontroli źródła lokalizacji projektu pojawia się tylko raz.<br /><br /> `Result from Step 3:`<br /><br /> Dodanie projektu zostało anulowane, projekt/rozwiązanie nie znajduje się pod kontrolą źródła i nadal są dostępne wszystkie menu kontroli źródła.|

### <a name="case-1b-open-solution-from-source-control"></a>Przypadek 1b. Otwórz rozwiązanie z kontroli źródła
 Ten przypadek testowy koncentruje się na otwieraniu rozwiązań z kontroli źródła.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Otwórz rozwiązanie zawierające projekt klienta z kontroli źródła|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Zamknij rozwiązanie.<br />4. Otwórz rozwiązanie z kontroli źródła w nowej lokalizacji.|Rozwiązanie/projekt otwarty z kontroli źródła.|
|Otwórz rozwiązanie zawierające projekt sieci Web lokalny lub IIS z kontroli źródła|1. Utwórz projekt sieci Web lokalny lub IIS.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Zamknij rozwiązanie.<br />4. Otwórz rozwiązanie z kontroli źródła w nowej lokalizacji.|Rozwiązanie/projekt otwarty z kontroli źródła.|
|Otwórz rozwiązanie zawierające projekt sieci Web zdalnej witryny z kontroli źródła|1. Utwórz projekt sieci Web zdalnej witryny.<br />2. Dodaj rozwiązanie do kontroli źródła. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />3. Zamknij rozwiązanie.<br />4. Otwórz rozwiązanie z kontroli źródła w nowej lokalizacji.|`Result from Step 2:`<br /><br /> Zdalna witryna sieci Web nie znajduje się pod kontrolą źródła.<br /><br /> `Result from Step 4:`<br /><br /> Rozwiązanie otwarte z kontroli źródła.<br /><br /> Zdalny projekt witryny został załadowany, ale nie znajduje się pod kontrolą źródła.|

### <a name="case-1c-add-solution-from-source-control"></a>Przypadek 1c: Dodawanie rozwiązania z kontroli źródła
 Ten przypadek testowy koncentruje się na dodawaniu rozwiązań z kontroli źródła.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Dodaj do pustego rozwiązania — jedno rozwiązanie projektu|1. Utwórz rozwiązanie pojedynczego projektu.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Zamknij rozwiązanie.<br />4. Utwórz drugie puste rozwiązanie.<br />5. Dodaj poprzednio kontrolowane rozwiązanie z kontroli źródła (**plik**, **Kontrola źródła**, **Dodaj projekt z kontroli źródła**).|Dodany projekt pojawia się w **Eksplorator rozwiązań** i jest zaewidencjonowany.|
|Dodaj do rozwiązania z pojedynczym projektem — pojedynczy projekt|1. Utwórz rozwiązanie z pojedynczym projektem.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Zamknij rozwiązanie.<br />4. Utwórz drugie puste rozwiązanie.<br />5. Dodaj poprzednio kontrolowane rozwiązanie z kontroli źródła (**plik**, **Kontrola źródła**, **Dodaj projekt z kontroli źródła**).|Dodany projekt pojawia się w **Eksplorator rozwiązań** i jest zaewidencjonowany.|
|Dodaj do rozwiązania — rozwiązanie dodane do kontroli źródła według wyboru|1. Utwórz rozwiązanie z projektem.<br />2. Dodaj tylko rozwiązanie do kontroli źródła jako zaznaczenie. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />3. Zamknij rozwiązanie.<br />4. Utwórz nowe rozwiązanie.<br />5. Dodaj poprzednio kontrolowane rozwiązanie z kontroli źródła (**plik**, **Kontrola źródła**, **Dodaj projekt z kontroli źródła**).|`Result from Step 2:`<br /><br /> Projekt nie znajduje się pod kontrolą źródła.<br /><br /> `Result from Step 5:`<br /><br /> Jeśli pierwsze rozwiązanie ma elementy rozwiązania, nie można ich dodać z kontroli źródła, więc nie są wyświetlane.<br /><br /> Projekt z pierwszego rozwiązania jest wyświetlany jako niedostępny.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
