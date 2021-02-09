---
title: 'Obszar testowy 5: zmiana kontroli źródła | Microsoft Docs'
description: Ten obszar testu wtyczki kontroli źródła obejmuje zmianę kontroli źródła przy użyciu polecenia Zmień kontrolę źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88dcc8e86da43f330c50ea478aaee572c1c3a060
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898137"
---
# <a name="test-area-5-change-source-control"></a>Obszar testowy 5: zmiana kontroli kodu źródłowego
Ten obszar testowania wtyczki kontroli źródła obejmuje zmianę kontroli źródła za pomocą polecenia **Zmień kontrolę źródła** .

 Polecenie **Zmień kontrolę źródła** udostępnia cztery podstawowe funkcje dla użytkownika:

- **Węglowodor**

   Zezwala użytkownikowi na ustanawianie lub ponowne Ustanawianie łącza kontroli źródła między rozwiązaniem/projektem i magazynem wersji.

- **Powiązania**

   Usuwa projekt/rozwiązanie z kontroli źródła dla poszczególnych połączeń.

- **Połącz/Rozłącz:**

  Przełącza podłączony lub offline stan kontrolowanego rozwiązania, które jest omówione w obszarze 3. Aby uzyskać więcej informacji, zobacz [obszar testowy 3: wyewidencjonowywanie/cofanie wyewidencjonowania](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Dostęp do menu poleceń
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]W przypadku testów użyto następującej ścieżki menu zintegrowanego środowiska deweloperskiego.

 Zmień kontrolę źródła:**plik**, **Kontrola źródła**, **zmiana kontroli źródła**.

## <a name="test-cases"></a>Przypadki testowe
 Poniżej wymieniono określone przypadki testowe dla obszaru testowego polecenia **zmiany kontroli źródła** .

### <a name="case-5a-bind"></a>Przypadek 5a: powiązanie
 Powiązanie umożliwia użytkownikowi dodawanie informacji o kontroli kodu źródłowego do wybranych projektów i rozwiązań. Użytkownik jest zazwyczaj monitowany o zidentyfikowanie projektu w kontroli źródła, do którego mają zostać dodane. Użytkownik nie może utworzyć nowego projektu w kontroli źródła w ramach tej operacji (kontrast z funkcją Dodaj do kontroli źródła).

| Akcja | Kroki testu | Oczekiwane wyniki do zweryfikowania |
| - | - | - |
| Powiąż z pustą lokalizacją | 1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Otwórz okno dialogowe **Zmienianie kontroli źródła** (**plik**, **Kontrola źródła**, **zmiana kontroli źródła**).<br />4. kliknij pozycję **Usuń powiązanie**.<br />5. Zaakceptuj okno dialogowe ostrzeżenia, jeśli zostanie wyświetlone.<br />6. Wybierz wszystkie elementy.<br />7. kliknij pozycję **bind**.<br />8. Przejdź do pustej lokalizacji w magazynie kontroli źródła.<br />9. kliknij przycisk **OK** , aby zamknąć okno dialogowe **Zmień kontrolę źródła** .<br />10. kliknij pozycję **Kontynuuj z tymi powiązaniami** w oknie dialogowym potwierdzenia.<br />11. Jeśli zostanie wyświetlone okno dialogowe ostrzeżenia, kliknij przycisk **OK** .<br />12. Zaewidencjonuj wszystko. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />13. Otwórz rozwiązanie z kontroli źródła w nowej lokalizacji. | `Result from Step 12:`<br /><br /> Rozwiązanie i projekt są powiązane z i zapisywane w nowym miejscu docelowym w sklepie z wersjami.<br /><br /> Pliki rozwiązania i projektu są zaewidencjonowane.<br /><br /> Hierarchia projektu magazynu wersji dopasowuje hierarchię folderów projektu na dysku.<br /><br /> `Result from Step 13:`<br /><br /> Wszystkie elementy projektu są pobierane. |
| Powiąż z lokalizacją, która jest zsynchronizowana z klientem | 1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Utwórz duplikat rozwiązania i projektu w magazynie wersji (udział i gałąź, jeśli używasz [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. Otwórz okno dialogowe **Zmienianie kontroli źródła** (**plik**, **Kontrola źródła**, **zmiana kontroli źródła**).<br />5. Usuń powiązanie wszystkiego.<br />6. kliknij przycisk **OK** , aby zamknąć okno dialogowe **Zmienianie kontroli źródła** .<br />7. ponownie otwórz okno dialogowe **Zmień kontrolę źródła** .<br />8. Zaznacz wszystko.<br />9. kliknij pozycję **bind**.<br />10. Przejdź do lokalizacji rozgałęzienia rozwiązania i projektu (z kroku 3)<br />11. kliknij przycisk **OK** , aby zamknąć okno dialogowe **Zmienianie kontroli źródła** .<br />12. Pobierz najnowszą rekursywnie dla wszystkich elementów. | Zawartość pliku po get jest taka sama jak przed get. |
| Powiąż z niezsynchronizowaną lokalizacją z klientem | 1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Utwórz duplikat rozwiązania i projektu w magazynie wersji (udział i gałąź, jeśli używasz [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. Zmodyfikuj pliki w oddziale projektu w sklepie z wersjami.<br />5. Otwórz okno dialogowe **Zmienianie kontroli źródła** (**plik**, **Kontrola źródła**, **zmiana kontroli źródła**).<br />6. Usuń powiązanie wszystkiego.<br />7. kliknij przycisk **OK** , aby zamknąć okno dialogowe **Zmienianie kontroli źródła** .<br />8. ponownie otwórz okno dialogowe **Zmień kontrolę źródła** .<br />9. Zaznacz wszystko.<br />10. kliknij pozycję **bind**.<br />11. Przejdź do lokalizacji rozgałęzienia dla rozwiązania i projektu.<br />12. kliknij przycisk **OK** , aby zamknąć okno dialogowe **Zmienianie kontroli źródła** .<br />13. Zaakceptuj okno dialogowe ostrzeżenia, jeśli zostanie wyświetlone.<br />14. Pobierz najnowszą rekursywnie dla wszystkich elementów. | Pliki zmodyfikowane w kroku 4 również są modyfikowane lokalnie. |
| Powiąż rozwiązanie, które nigdy nie podlega kontroli źródła | 1. Utwórz pusty folder w kontroli źródła.<br />2. Utwórz projekt klienta.<br />3. Otwórz okno dialogowe **Zmienianie kontroli źródła** (**plik**, **Kontrola źródła**, **zmiana kontroli źródła**).<br />4. Powiąż rozwiązanie z pustą lokalizacją w kontroli źródła.<br />5. kliknij przycisk **OK** , aby zamknąć okno dialogowe **Zmienianie kontroli źródła** .<br />6. kliknij pozycję **Kontynuuj z tymi powiązaniami** w oknie dialogowym potwierdzenia.<br />7. Jeśli zostanie wyświetlone okno dialogowe ostrzeżenia, kliknij przycisk **OK** . | Rozwiązanie zostało dodane do kontroli źródła.<br /><br /> Rozwiązanie i projekt są wyewidencjonowane. |
| Anuluj powiązanie | 1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Otwórz okno dialogowe Zmienianie kontroli źródła.<br />4. Usuń powiązanie wszystkiego.<br />5. kliknij przycisk **OK** , aby zamknąć okno dialogowe. Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />6. Otwórz ponownie okno dialogowe **Zmień kontrolę źródła** .<br />7. Powiąż z niepowiązaną lokalizacją.<br />8. kliknij przycisk **Anuluj**. | `Result from Step 5:`<br /><br /> Rozwiązanie nie znajduje się już pod kontrolą źródła<br /><br /> `Result from Step 8:`<br /><br /> Rozwiązanie nadal nie znajduje się pod kontrolą źródła. |

### <a name="case-5b-unbind"></a>Przypadek 5B: Usuwanie powiązania
 Unbind usuwa informacje o kontroli kodu źródłowego z projektów i ich rozwiązania. Uwzględnione projekty i rozwiązania są oparte na kombinacji wyboru użytkownika i sposobie dodawania elementów do kontroli źródła.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Usuń powiązanie rozwiązania zawierającego jeden system plików lub lokalny projekt sieci Web usług IIS i jeden projekt klienta|1. Utwórz system plików lub lokalny projekt sieci Web usług IIS.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj nowy projekt klienta do rozwiązania.<br />4. Zaakceptuj Wyewidencjonuj rozwiązanie, jeśli zostanie wyświetlony monit.<br />5. Otwórz okno dialogowe **Zmienianie kontroli źródła** .<br />6. kliknij pozycję **Usuń powiązanie**.<br />7. kliknij przycisk **OK** , aby zamknąć okno dialogowe.<br />8. próba wyewidencjonowania rozwiązania, projektu, elementów rozwiązania, elementów projektu.|Rozwiązanie i projekty nie znajdują się pod kontrolą źródła.<br /><br /> Polecenia menu kontroli źródła nie są wyświetlane.|
|Anuluj powiązanie powiązania|1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Otwórz okno dialogowe **Zmienianie kontroli źródła** .<br />4. kliknij pozycję **Usuń powiązanie wszystkiego**.<br />5. kliknij przycisk **Anuluj**.|Rozwiązanie jest pod kontrolą źródła.|

### <a name="case-5c-rebind"></a>Przypadek 5c: rebind
 Rebind jest po prostu połączeniem powiązania i powiązania — proces ponownego powiązania projektu/rozwiązania, który był wcześniej objęty kontrolą źródła i został anulowany.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Ponowne wiązanie rozwiązania i projektów bez zamykania okna dialogowego **Zmień kontrolę źródła**|1. Utwórz projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Otwórz okno dialogowe **Zmienianie kontroli źródła** .<br />4. kliknij pozycję **Usuń powiązanie**.<br />5. Zaznacz wszystkie wiersze.<br />6. kliknij pozycję **bind**.<br />7. kliknij przycisk **OK** , aby zamknąć okno dialogowe **Zmienianie kontroli źródła** .<br />8. Zaakceptuj wyewidencjonowanie, jeśli zostanie wyświetlony monit.|Rozwiązanie i projekt znajdują się pod kontrolą źródła.|
|Ponownie powiązać projekt tylko bez zamykania okna dialogowego **Zmień kontrolę źródła**|1. Utwórz projekt.<br />2. Dodaj tylko projekt do kontroli źródła przy użyciu programu (kontrola źródła plików >, >dodać wybrane projekty do kontroli źródła.<br />3. Otwórz okno dialogowe Zmienianie kontroli źródła.<br />4. Usuń powiązanie tylko projektu.<br />5. Powiąż tylko projekt.|Rozwiązanie pozostaje niekontrolowane.<br /><br /> Projekt pozostaje kontrolowany.|
|Ponownie powiązać rozwiązanie tylko bez zamykania okna dialogowego **Zmień kontrolę źródła**|1. Utwórz projekt.<br />2. Dodaj tylko rozwiązanie do kontroli źródła przy użyciu (**plik**, **Kontrola źródła**, **Dodaj wybrane projekty do kontroli źródła**.<br />3. Otwórz okno dialogowe **Zmienianie kontroli źródła** .<br />4. Usuń powiązanie tylko rozwiązania (nie zamykaj okna dialogowego **Zmień kontrolę źródła** ).<br />5. Powiąż tylko rozwiązanie.<br />6. kliknij przycisk **OK** , aby zamknąć okno dialogowe.<br />7. Sprawdź elementy rozwiązania i rozwiązania (jeśli istnieją).|Rozwiązanie pozostaje kontrolowane.<br /><br /> Projekt pozostaje niekontrolowany.|
|Ponownie powiązać rozwiązanie/projekt tylko wtedy, gdy znajduje się on w tym samym katalogu|1. Utwórz projekt.<br />2. Dodaj tylko projekt do kontroli źródła przy użyciu (**plik**, **Kontrola źródła**, **Dodaj wybrane projekty do kontroli źródła**.<br />3. Zamknij rozwiązanie.<br />4. Utwórz nowe rozwiązanie z co najmniej dwoma projektami.<br />5. Dodaj rozwiązanie do kontroli źródła.<br />6. Dodaj projekt utworzony w kroku 1 z kontroli źródła.<br />7. Zaakceptuj wyewidencjonowanie rozwiązania, jeśli zostanie wyświetlony monit.<br />8. Zaewidencjonuj całe rozwiązanie.<br />9. Otwórz okno dialogowe **Zmienianie kontroli źródła** .<br />10. Wybierz dodany projekt (z kroku 6) i kliknij pozycję **Usuń powiązanie**.<br />11. kliknij przycisk **OK** , aby zamknąć okno dialogowe.<br />12. Zaakceptuj wyewidencjonowanie, jeśli zostanie wyświetlony monit.<br />13. ponownie otwórz okno dialogowe **Zmień kontrolę źródła** .<br />14. Wybierz dodany projekt (z kroku 6) i kliknij pozycję **bind**.<br />15. Wybierz oryginalną lokalizację.|Rozwiązanie i projekty nadal są kontrolowane.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
