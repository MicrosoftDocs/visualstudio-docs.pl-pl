---
title: 'Obszar testowy 5: Zmień kontrolę źródła | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 83928a2b28b32d7e1ee11475a7693f8f11483cad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942635"
---
# <a name="test-area-5-change-source-control"></a>Obszar testowy 5: Zmień kontrolę źródła
Ten obszar testowy wtyczki kontroli źródła obejmuje zmiany kontroli źródła, za pośrednictwem **Zmień kontrolę źródła** polecenia.  

 **Zmień kontrolę źródła** polecenie dostarcza cztery podstawowe funkcje dla użytkownika:  

- **Powiązania:**  

   Umożliwia użytkownikowi określić lub ponownie ustanowić połączenia kontroli źródła między rozwiązania/projektu i magazynu w wersji.  

- **Usuwanie powiązania:**  

   Usuwa projekt/rozwiązanie z kontrolą źródła w poszczególnych połączeń.  

- **Łączenie/rozłączanie połączeń:**  

  Włącza lub wyłącza połączonych lub offline stan rozwiązania kontrolowanego, co zostało omówione w obszarze 3. Aby uzyskać więcej informacji, zobacz [3 obszaru testu: Zapoznaj się z / Cofnij wyewidencjonowanie](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  

## <a name="command-menu-access"></a>Dostęp do Menu polecenia  
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego rozwoju środowiska menu Ścieżka jest używana w przypadkach testowych.  

 Zmień kontrolę źródła:**pliku**, **kontroli źródła**, **Zmień kontrolę źródła**.  

## <a name="test-cases"></a>Przypadki testowe  
 Poniżej przedstawiono określonych przypadków testowych dla **Zmień kontrolę źródła** polecenia obszar testowy.  

### <a name="case-5a-bind"></a>Wielkość 5a: powiązania  
 Powiązania zezwala użytkownikowi na dodawanie informacji o kontroli kodu źródłowego do wybranych projektów i rozwiązań. Użytkownik jest zwykle monitowany do identyfikowania projektu w kontroli źródła, do której są dodane. Użytkownik nie może utworzyć nowy projekt w kontroli źródła w ramach tej operacji (kontrast za pomocą Dodaj do kontroli źródła).  


| Akcja | Kroki testu | Oczekiwanych wyników, aby sprawdzić |
| - | - | - |
| Powiąż z pustą lokalizację | 1.  Utwórz projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Otwórz **Zmień kontrolę źródła** okno dialogowe (**pliku**, **kontroli źródła**, **Zmień kontrolę źródła**).<br />4.  Kliknij przycisk **Unbind**.<br />5.  Jeśli wygląda na to, należy zaakceptować okno dialogowe ostrzeżenia.<br />6.  Wybierz wszystkie elementy.<br />7.  Kliknij przycisk **powiązać**.<br />8.  Przejdź do lokalizacji pusty w magazynie kontroli źródła.<br />9. Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />10. Kliknij przycisk **Kontynuuj z tymi powiązaniami** w oknie dialogowym potwierdzenia.<br />11. Kliknij przycisk **OK** w oknie dialogowym ostrzeżenia, jeśli zostanie wyświetlona.<br />12. Zaewidencjonuj wszystko. Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />13. Otwórz rozwiązanie z kontroli źródła do nowej lokalizacji. | `Result from Step 12:`<br /><br /> Rozwiązania i projektu są powiązane i zapisywany nowy obiekt docelowy magazyn wersji.<br /><br /> Rozwiązanie i pliki projektu są ewidencjonowane.<br /><br /> Hierarchia projektów Sklepu wersji pasuje do hierarchii folderów projektu na dysku.<br /><br /> `Result from Step 13:`<br /><br /> Wszystkie elementy projektu zostaną pobrane. |
| Powiąż z lokalizacji, która jest zsynchronizowany z klienta | 1.  Utwórz projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Utworzenie duplikatu rozwiązania i projektu w magazynie wersji (Udostępnianie i gałęzi, jeśli za pomocą [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Otwórz **Zmień kontrolę źródła** okno dialogowe (**pliku**, **kontroli źródła**, **Zmień kontrolę źródła**).<br />5.  Usunąć wszystkie powiązania.<br />6.  Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />7.  Otwórz ponownie **Zmień kontrolę źródła** okno dialogowe.<br />8.  Zaznacz wszystko.<br />9. Kliknij przycisk **powiązać**.<br />10. Przejdź do lokalizacji rozgałęziony rozwiązania i projektu (z kroku 3)<br />11. Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />12. Pobierz najnowsze rekursywnie dla wszystkich elementów. | Zawartość pliku po get jest taka sama, jak przed get. |
| Powiąż z lokalizacji, która nie jest zsynchronizowany z klientem | 1.  Utwórz projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Utworzenie duplikatu rozwiązania i projektu w magazynie wersji (Udostępnianie i gałęzi, jeśli za pomocą [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Zmodyfikuj pliki w projekcie rozgałęzione w magazynie wersji.<br />5.  Otwórz **Zmień kontrolę źródła** okno dialogowe (**pliku**, **kontroli źródła**, **Zmień kontrolę źródła**).<br />6.  Usunąć wszystkie powiązania.<br />7.  Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />8.  Otwórz ponownie **Zmień kontrolę źródła** okno dialogowe.<br />9. Zaznacz wszystko.<br />10. Kliknij przycisk **powiązać**.<br />11. Przejdź do rozgałęzione lokalizację dla rozwiązania i projektu.<br />12. Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />13. Jeśli wygląda na to, należy zaakceptować okno dialogowe ostrzeżenia.<br />14. Pobierz najnowsze cyklicznego dla wszystkich elementów. | Pliki, które zostały zmodyfikowane w kroku 4 również są modyfikowane lokalnie. |
| Powiąż rozwiązania, które było nigdy nie pod kontrolą źródła | 1.  Utwórz pusty folder w kontroli źródła.<br />2.  Utwórz projekt klienta.<br />3.  Otwórz **Zmień kontrolę źródła** okno dialogowe (**pliku**, **kontroli źródła**, **Zmień kontrolę źródła**).<br />4.  Powiązać rozwiązanie z pustą lokalizację w kontroli źródła.<br />5.  Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />6.  Kliknij przycisk **Kontynuuj z tymi powiązaniami** w oknie dialogowym potwierdzenia.<br />7.  Kliknij przycisk **OK** w oknie dialogowym ostrzeżenia, jeśli zostanie wyświetlona. | Rozwiązanie zostanie dodany do kontroli źródła.<br /><br /> Rozwiązania i projektu są wyewidencjonowane. |
| Anuluj powiązania | 1.  Utwórz projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Otwórz okno dialogowe zmiana kontroli źródła.<br />4.  Usunąć wszystkie powiązania.<br />5.  Kliknij przycisk **OK** przycisk, aby zamknąć okno dialogowe. Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />6.  Otwórz ponownie **Zmień kontrolę źródła** okno dialogowe.<br />7.  Powiąż z niepowiązanych lokalizacji.<br />8.  Kliknij przycisk **anulować**. | `Result from Step 5:`<br /><br /> Rozwiązanie nie jest już pod kontrolą źródła<br /><br /> `Result from Step 8:`<br /><br /> Rozwiązanie jest nadal nie pod kontroli źródła. |

### <a name="case-5b-unbind"></a>Wielkość 5b: Usuń powiązanie  
 Usuń powiązanie informacje o kontroli kodu źródłowego powoduje usunięcie z projektów i ich rozwiązania. Dotyczy projekty i rozwiązania są oparte na kombinacji wybór użytkownika i jak elementy zostały dodane do kontroli źródła.  

|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Usuń powiązanie rozwiązanie zawierające jeden System plików lub lokalny projekt sieci Web usług IIS i jeden klient z projektu|1.  Utwórz System plików lub lokalny projekt sieci Web usług IIS.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj nowy projekt klienta do rozwiązania.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować zapoznaj się z rozwiązania.<br />5.  Otwórz **Zmień kontrolę źródła** okno dialogowe.<br />6.  Kliknij przycisk **Unbind**.<br />7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.<br />8.  Próba zapoznaj się z rozwiązania, projektu, elementy rozwiązania, elementy projektu.|Rozwiązanie i projekty nie są pod kontrolą źródła.<br /><br /> Polecenia menu kontroli źródła nie są wyświetlane.|  
|Usuń powiązanie Anuluj|1.  Utwórz projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Otwórz **Zmień kontrolę źródła** okno dialogowe.<br />4.  Kliknij przycisk **usunąć wszystkie powiązania**.<br />5.  Kliknij przycisk **anulować**.|Rozwiązanie jest pod kontrolą źródła.|  

### <a name="case-5c-rebind"></a>W przypadku 5c: ponowne wiązanie  
 Ponowne wiązanie jest po prostu kombinacją Usuń powiązanie i powiąż — proces ponownego wiązania projekt/rozwiązanie, poprzednio pod kontrolą źródła, która została niepowiązanej.  

|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Ponownie powiązać rozwiązanie i projekty nie zamykając **Zmień kontrolę źródła** okno dialogowe|1.  Utwórz projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Otwórz **Zmień kontrolę źródła** okno dialogowe.<br />4.  Kliknij przycisk **Unbind**.<br />5.  Wybierz wszystkie wiersze.<br />6.  Kliknij przycisk **powiązać**.<br />7.  Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />8.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowania.|Rozwiązania i projektu są pod kontrolą źródła.|  
|Ponownie powiązać projekt tylko bez zamykania **Zmień kontrolę źródła** okno dialogowe|1.  Utwórz projekt.<br />2.  Dodaj tylko projekt do kontroli źródła przy użyciu (Plik -> źródło sterowania -> Dodaj wybrane projekty do kontroli źródła.<br />3.  Otwórz okno dialogowe zmiana kontroli źródła.<br />4.  Usuń powiązanie tylko dla projektu.<br />5.  Powiąż tylko dla projektu.|Rozwiązanie nadal będzie niekontrolowany.<br /><br /> Projekt pozostaje kontrolowany.|  
|Ponownie powiązać rozwiązanie tylko bez zamykania **Zmień kontrolę źródła** okno dialogowe|1.  Utwórz projekt.<br />2.  Dodaj tylko rozwiązanie do kontroli źródła przy użyciu (**pliku**, **kontroli źródła**, **Dodaj wybrane projekty do kontroli źródła**.<br />3.  Otwórz **Zmień kontrolę źródła** okno dialogowe.<br />4.  Usuń powiązanie tylko rozwiązanie (nie zamykaj **Zmień kontrolę źródła** okno dialogowe.)<br />5.  Powiąż tylko rozwiązania.<br />6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.<br />7.  Zapoznaj się z rozwiązania i elementami rozwiązania, (jeśli istnieje)|Rozwiązanie nadal będzie kontrolowany.<br /><br /> Projekt pozostaje niekontrolowany.|  
|Ponownie powiązać rozwiązania/projektu, tylko w tym samym katalogu|1.  Utwórz projekt.<br />2.  Dodaj tylko projekt do kontroli źródła przy użyciu (**pliku**, **kontroli źródła**, **Dodaj wybrane projekty do kontroli źródła**.<br />3.  Zamknij rozwiązanie.<br />4.  Utwórz nowe rozwiązanie z co najmniej dwa projekty.<br />5.  Dodaj rozwiązanie do kontroli źródła.<br />6.  Dodaj projekt utworzony w kroku 1 z kontroli źródła.<br />7.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowanie rozwiązania.<br />8.  Sprawdź w całym rozwiązaniu.<br />9. Otwórz **Zmień kontrolę źródła** okno dialogowe.<br />10. Wybierz projekt dodano (z kroku 6), a następnie kliknij przycisk **Unbind**.<br />11. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.<br />12. Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowanie.<br />13. Otwórz ponownie **Zmień kontrolę źródła** okno dialogowe.<br />14. Wybierz projekt dodano (z kroku 6), a następnie kliknij przycisk **powiązać**.<br />15. Wybierz lokalizację, oryginalnym.|Rozwiązanie i projekty pozostaną kontrolowany.|  

## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)