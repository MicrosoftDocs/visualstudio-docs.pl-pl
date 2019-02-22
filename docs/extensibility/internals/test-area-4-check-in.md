---
title: 'Obszar testowy 4: Zaewidencjonuj | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2529b22d7039101f83952b3390221af5b78922b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605110"
---
# <a name="test-area-4-check-in"></a>Obszar testowy 4: Zaewidencjonuj
Ten obszar testowy wtyczki kontroli źródła obejmuje wysyłanie zaktualizowanych elementów do magazynu wersji za pomocą **Zaewidencjonuj** polecenia.

## <a name="command-menu-access"></a>Dostęp do Menu polecenia
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ścieżki menu środowiska zintegrowanego rozwoju są używane w przypadkach testowych.

##### <a name="check-in"></a>Zamelduj się:
 **Plik**, **kontroli źródła**, **zaewidencjonować**.

 **Plik**, **zaewidencjonować**.

 Menu skrótów **Zaewidencjonuj**.

## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie.

-   Projekty i pliki dodane do rozwiązania lub projektu objętego kontrolą źródła są wyświetlane w **Zaewidencjonuj** okno dialogowe i **oczekujące elementy do zaewidencjonowania** okna.

-   Po zaewidencjonowaniu dodane elementy są wyświetlane w kontroli źródła.

-   Po zaewidencjonowaniu zaktualizowane elementy są prawidłowo wersjonowanych w magazynie.

## <a name="test-cases"></a>Przypadki testowe
 Poniżej przedstawiono określonych przypadków testowych dla obszaru testów zaewidencjonowania.

### <a name="case-4a-modified-items"></a>Wielkość 4a: Zmodyfikowane elementy
 Opisano sposób używania sprawdzenie w działaniu można zaktualizować pliku objętego kontrolą źródła, który został zmodyfikowany.

|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|
|------------|----------------|--------------------------------|
|Zmodyfikuj plik tekstowy, który został wyewidencjonowany, sprawdź w pliku tylko (**Zaewidencjonuj** okno dialogowe)|1.  Utwórz nowy projekt za pomocą pliku tekstowego.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z i zmodyfikuj plik tekstowy.<br />4.  Sprawdź plik w folderze za pomocą okna dialogowego zaewidencjonowania (**pliku**, **kontroli źródła**, **Zaewidencjonuj**).|Typowe oczekiwane zachowanie.|
|Zmodyfikuj plik tekstowy, który został wyewidencjonowany, sprawdź w pliku tylko (**oczekujące elementy do zaewidencjonowania** okna)|1.  Utwórz nowy projekt za pomocą pliku tekstowego.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z i zmodyfikuj plik tekstowy.<br />4.  Zaewidencjonuj za pośrednictwem **oczekujące elementy do zaewidencjonowania** okna.|Typowe oczekiwane zachowanie.|

### <a name="case-4b-adding-files"></a>Wielkość 4b: Trwa dodawanie plików
 Podczas dodawania pliku do projektu lub elementu do rozwiązania, projektu lub rozwiązania, należy również zmienić. Tym samym pliku nadrzędnego również jest wyewidencjonowany i muszą zostać zaewidencjonowane, aby zakończyć dodawanie.

|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|
|------------|----------------|--------------------------------|
|Dodaj plik tekstowy i zaewidencjonuj wszystko przed (**Zaewidencjonuj** okno dialogowe)|1.  Utwórz nowy projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj plik tekstowy do projektu.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowania projektu.<br />5.  Wybierz rozwiązanie w **Eksploratora rozwiązań**.<br />6.  Sprawdź **Zaewidencjonuj** okno dialogowe.|Typowe oczekiwane zachowanie.|
|Dodaj plik tekstowy i zaewidencjonuj wszystko przed (**oczekujące elementy do zaewidencjonowania** okna)|1.  Utwórz nowy projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj plik tekstowy do projektu.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowania projektu.<br />5.  Zaewidencjonuj rozwiązanie z **oczekujące elementy do zaewidencjonowania** okna.|Typowe oczekiwane zachowanie.|

### <a name="case-4c-adding-projects"></a>W przypadku 4c: Dodawanie projektów
 Po dodaniu projektu do rozwiązania, należy także zmienić rozwiązania. Dlatego pliku rozwiązania jest wyewidencjonowany również i muszą zostać zaewidencjonowane, aby zakończyć dodawanie.

|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|
|------------|----------------|--------------------------------|
|Dodaj projekt do puste rozwiązanie pod kontrolą źródła (**Zaewidencjonuj** okno dialogowe)|1.  Utwórz puste rozwiązanie.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj nowy projekt.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowanie rozwiązania.<br />5.  Sprawdź **Zaewidencjonuj** okno dialogowe.|Typowe oczekiwane zachowanie.|
|Dodaj projekt do puste rozwiązanie pod kontrolą źródła (**oczekujące elementy do zaewidencjonowania** okna)|1.  Utwórz puste rozwiązanie.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj nowy projekt.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowanie rozwiązania.<br />5.  Zaewidencjonuj rozwiązanie z **oczekujące elementy do zaewidencjonowania** okna.|Typowe oczekiwane zachowanie.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)