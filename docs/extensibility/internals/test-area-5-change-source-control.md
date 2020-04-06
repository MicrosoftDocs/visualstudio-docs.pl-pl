---
title: 'Obszar badania 5: Zmiana kontroli źródła | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1c0df31fbecd532e6a5f7f317730cd995cd8225
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704524"
---
# <a name="test-area-5-change-source-control"></a>Obszar testowy 5: zmienianie kontroli kodu źródłowego
Ten obszar testu wtyczki kontroli źródła obejmuje zmianę kontroli źródła za pomocą polecenia **Zmień pozycję kontroli źródła.**

 Polecenie **Zmień formant źródła** udostępnia użytkownikowi cztery podstawowe funkcje:

- **Powiązać:**

   Umożliwia użytkownikowi ustanowienie lub ponowne ustanowienie łącza kontroli źródła między rozwiązaniem/projektem a magazynem wersji.

- **Unbind:**

   Usuwa projekt/rozwiązanie z kontroli źródła na podstawie połączenia.

- **Podłącz/Rozłącz:**

  Przełącza stan połączenia lub offline kontrolowanego rozwiązania, który jest objęty obszarem 3. Aby uzyskać więcej informacji, zobacz [Obszar testu 3: Wyewidencjonuj/Cofnij wyewidencjonowanie](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Dostęp do menu polecenia
 W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przypadkach testowych używana jest następująca ścieżka menu zintegrowanego środowiska programistycznego.

 Zmień formant źródła:**plik**, **kontrola źródła,** **zmień formant źródła**.

## <a name="test-cases"></a>Przypadki testowe
 Poniżej przedstawiono konkretne przypadki testowe dla obszaru testu polecenia **Zmień kontrolę źródła.**

### <a name="case-5a-bind"></a>Przypadek 5a: Bind
 Powiązanie umożliwia użytkownikowi dodawanie informacji o kontroli kodu źródłowego do wybranych projektów i rozwiązań. Użytkownik jest zazwyczaj monitowany o zidentyfikowanie projektu w formancie źródła, do którego mają zostać dodane. Użytkownik nie może utworzyć nowego projektu w kontroli źródła w ramach tej operacji (kontrast z Dodaj do kontroli źródła).

| Akcja | Etapy testu | Oczekiwane wyniki do zweryfikowania |
| - | - | - |
| Powiąż się na pustej lokalizacji | 1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Okno dialogowe **Otwieranie formantu źródła** **(plik,** **kontrola źródła,** **zmienianie kontroli źródła).**<br />4. Kliknij **przycisk Odłącz .**<br />5. Zaakceptuj okno dialogowe z ostrzeżeniem, jeśli się pojawi.<br />6. Wybierz wszystkie elementy.<br />7. Kliknij pozycję **Powiąż**.<br />8. Przejdź do pustej lokalizacji w magazynie kontroli źródła.<br />9. Kliknij **przycisk OK,** aby zamknąć okno dialogowe **Zmienianie formantu źródła.**<br />10. Kliknij przycisk **Kontynuuj z tymi powiązaniami** w oknie dialogowym potwierdzenia.<br />11. Kliknij **przycisk OK** w oknie dialogowym z ostrzeżeniem, jeśli się pojawi.<br />12. Zamelduj się we wszystkim. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />13. Otwarte rozwiązanie od kontroli źródła do nowej lokalizacji. | `Result from Step 12:`<br /><br /> Rozwiązanie i projekt są powiązane i zapisywane do nowego obiektu docelowego w magazynie wersji.<br /><br /> Pliki rozwiązań i projektów są zaewidencjonowane.<br /><br /> Hierarchia projektu magazynu wersji dopasowuje hierarchię folderów projektu na dysku.<br /><br /> `Result from Step 13:`<br /><br /> Wszystkie elementy projektu są pobierane. |
| Powiązanie z lokalizacją zsynchronizowanej z klientem | 1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Utwórz duplikat rozwiązania i projektu w magazynie [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]wersji (Udostępnij i Oddział, jeśli używasz ).<br />4. Otwórz okno dialogowe **Formant źródła zmian** **(Plik,** **Kontrola źródła,** **Zmień kontrolę źródła).**<br />5. Odłącz wszystko.<br />6. Kliknij **przycisk OK,** aby zamknąć okno dialogowe **Zmienianie kontroli źródła.**<br />7. Otwórz ponownie okno dialogowe **Kontrola źródła zmian.**<br />8. Wybierz wszystkie.<br />9. Kliknij pozycję **Powiąż**.<br />10. Przejdź do rozgałęzione lokalizacji rozwiązania i projektu (od kroku 3)<br />11. Kliknij **przycisk OK,** aby zamknąć okno dialogowe **Zmienianie formantu źródła.**<br />12. Pobierz najnowsze rekursywnie dla wszystkich przedmiotów. | Zawartość pliku po dokonaniu jest taka sama, jak przed uzyskaniem. |
| Powiązanie z lokalizacją, która nie jest zsynchronizowana z klientem | 1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Utwórz duplikat rozwiązania i projektu w magazynie [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]wersji (Udostępnij i Oddział, jeśli używasz ).<br />4. Modyfikuj pliki w rozgałęziony projekt w magazynie wersji.<br />5. Okno dialogowe **Otwieranie formantu źródła** **(plik,** **kontrola źródła,** **zmienianie kontroli źródła).**<br />6. Odłącz wszystkie.<br />7. Kliknij **przycisk OK,** aby zamknąć okno dialogowe **Zmienianie kontroli źródła.**<br />8. Otwórz ponownie okno dialogowe **Kontrola źródła zmian.**<br />9. Wybierz wszystkie.<br />10. Kliknij pozycję **Powiąż**.<br />11. Przejdź do rozgałęzione lokalizacji dla rozwiązania i projektu.<br />12. Kliknij przycisk **OK,** aby zamknąć okno dialogowe **Zmienianie formantu źródła.**<br />13. Zaakceptuj okno dialogowe Ostrzeżenie, jeśli się pojawi.<br />14. Pobierz najnowsze cykliczne dla wszystkich przedmiotów. | Pliki, które zostały zmodyfikowane w kroku 4 są również modyfikowane lokalnie. |
| Rozwiązanie bind, które nigdy nie było pod kontrolą źródła | 1. Utwórz pusty folder w formancie źródłowym.<br />2. Utwórz projekt klienta.<br />3. Okno dialogowe **Otwieranie formantu źródła** **(plik,** **kontrola źródła,** **zmienianie kontroli źródła).**<br />4. Powiąż rozwiązanie z pustą lokalizacją w kontroli źródła.<br />5. Kliknij **przycisk OK,** aby zamknąć okno dialogowe **Zmienianie formantu źródła.**<br />6. Kliknij przycisk **Kontynuuj z tymi powiązaniami** w oknie dialogowym potwierdzenia.<br />7. Kliknij **przycisk OK** w oknie dialogowym z ostrzeżeniem, jeśli się pojawi. | Rozwiązanie jest dodawane do kontroli źródła.<br /><br /> Rozwiązanie i projekt są wyewidencjonowane. |
| Anuluj powiązanie | 1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Otwórz okno dialogowe Zmień pozycję Kontrolka źródła.<br />4. Odłącz wszystko.<br />5. Kliknij przycisk **OK,** aby zamknąć okno dialogowe. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />6. Otwórz ponownie okno dialogowe **Zmień pozycję Kontrolki źródła.**<br />7. Powiązanie z niepowiązaną lokalizacją.<br />8. Kliknij **przycisk Anuluj**. | `Result from Step 5:`<br /><br /> Rozwiązanie nie jest już pod kontrolą źródła<br /><br /> `Result from Step 8:`<br /><br /> Rozwiązanie nadal NIE jest pod kontrolą źródła. |

### <a name="case-5b-unbind"></a>Przypadek 5b: Unbind
 Unbind usuwa informacje o kontroli kodu źródłowego z projektów i ich rozwiązania. Projekty i rozwiązanie, których dotyczy problem, są oparte na kombinacji wyboru użytkownika i sposobu, w jaki elementy zostały dodane do kontroli źródła.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Rozwiązanie unbind zawierające jeden system plików lub lokalny projekt sieci Web usług IIS i jeden projekt klienta|1. Utwórz system plików lub lokalny projekt sieci Web usług IIS.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj nowy projekt klienta do rozwiązania.<br />4. Zaakceptuj wyewidencjonowanie rozwiązania, jeśli zostanie wyświetlony monit.<br />5. Otwórz okno dialogowe **Zmień pozycję Kontrolka źródła.**<br />6. Kliknij **przycisk Odłącz .**<br />7. Kliknij **przycisk OK,** aby zamknąć okno dialogowe.<br />8. Spróbuj sprawdzić rozwiązanie, projekt, elementy rozwiązania, elementy projektu.|Rozwiązania i projekty NIE są pod kontrolą źródła.<br /><br /> Polecenia menu Kontrola źródła nie są wyświetlane.|
|Anuluj odłączyć|1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Otwórz okno dialogowe **Zmień pozycję Kontrolka źródła.**<br />4. Kliknij przycisk **Odłącz wszystkie**.<br />5. Kliknij **przycisk Anuluj**.|Rozwiązanie jest pod kontrolą źródła.|

### <a name="case-5c-rebind"></a>Przypadek 5c: Rebind
 Rebind jest po prostu kombinacją unbind i bind — proces ponownego wiązania projektu / rozwiązania, który był wcześniej pod kontrolą źródła i był niezwiązany.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Ponowne wiązawanie rozwiązań i projektów bez zamykania okna dialogowego **Zmień formant źródła**|1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Otwórz okno dialogowe **Zmień pozycję Kontrolka źródła.**<br />4. Kliknij **przycisk Odłącz .**<br />5. Zaznacz wszystkie wiersze.<br />6. Kliknij pozycję **Powiąż**.<br />7. Kliknij **przycisk OK,** aby zamknąć okno dialogowe **Zmienianie formantu źródła.**<br />8. Zaakceptuj wyewidencjonowanie, jeśli zostanie wyświetlony monit.|Rozwiązanie i projekt są pod kontrolą źródła.|
|Ponowne powiązanie projektu tylko bez zamykania okna dialogowego **Zmień formant źródła**|1. Utwórz projekt.<br />2. Dodaj tylko projekt do kontroli źródła przy użyciu (File->Source Control->Dodaj wybrane projekty do kontroli źródła.<br />3. Otwórz okno dialogowe Zmień pozycję Kontrolka źródła.<br />4. Odłączyć tylko projekt.<br />5. Powiąż tylko projekt.|Rozwiązanie pozostaje niekontrolowane.<br /><br /> Projekt pozostaje kontrolowany.|
|Ponowne wiązawanie rozwiązania tylko bez zamykania okna dialogowego **Zmień formant źródła**|1. Utwórz projekt.<br />2. Dodaj tylko rozwiązanie do kontroli źródła za pomocą **(Plik**, **Kontrola źródła**, Dodaj wybrane projekty do **kontroli źródła**.<br />3. Otwórz okno dialogowe **Zmień pozycję Kontrolka źródła.**<br />4. Odłączyć tylko rozwiązanie (nie zamykaj okna dialogowego **Zmień formant źródła).**<br />5. Powiąż tylko roztwór.<br />6. Kliknij **przycisk OK,** aby zamknąć okno dialogowe.<br />7. Sprawdź rozwiązania i elementy rozwiązania (jeśli istnieją.)|Roztwór pozostaje kontrolowany.<br /><br /> Projekt pozostaje niekontrolowany.|
|Ponowne wiązki rozwiązania/projektu tylko wtedy, gdy w tym samym katalogu|1. Utwórz projekt.<br />2. Dodaj tylko projekt do kontroli źródła za pomocą **(Plik**, **Kontrola źródła**, Dodaj wybrane projekty do **kontroli źródła**.<br />3. Zamknąć roztwór.<br />4. Utwórz nowe rozwiązanie z co najmniej dwoma projektami.<br />5. Dodaj rozwiązanie do kontroli źródła.<br />6. Dodaj projekt utworzony w kroku 1 z kontroli źródła.<br />7. Zaakceptuj wyewidencjonowanie rozwiązania, jeśli zostanie wyświetlony monit.<br />8. Zaewidencjonuj całe rozwiązanie.<br />9. Otwórz okno dialogowe **Zmień formant źródła.**<br />10. Wybierz dodany projekt (z kroku 6) i kliknij przycisk **Odłącz**.<br />11. Kliknij **przycisk OK,** aby zamknąć okno dialogowe.<br />12. Zaakceptuj wyewidencjonowanie, jeśli zostanie wyświetlony monit.<br />13. Otwórz ponownie okno dialogowe **Kontrola źródła zmian.**<br />14. Wybierz dodany projekt (z kroku 6) i kliknij przycisk **Powiąż**.<br />15. Wybierz oryginalną lokalizację.|Rozwiązania i projekty pozostają kontrolowane.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
