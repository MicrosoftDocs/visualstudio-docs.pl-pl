---
title: 'Obszar testowy 4: Sprawdź plik w folderze | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 97a610325a5165a1de2cc50fede5bbabf182ef5e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783308"
---
# <a name="test-area-4-check-in"></a>Obszar testowy 4: zaewidencjonowanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ten obszar testowy wtyczki kontroli źródła obejmuje wysyłanie zaktualizowanych elementów do magazynu wersji za pomocą **Zaewidencjonuj** polecenia.  
  
## <a name="command-menu-access"></a>Dostęp do Menu polecenia  
 Następujące [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ścieżki menu środowiska zintegrowanego rozwoju są używane w przypadkach testowych.  
  
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
  
### <a name="case-4a-modified-items"></a>Zamierzone, Zapisz 4a: zmodyfikowane elementy  
 Opisano sposób używania sprawdzenie w działaniu można zaktualizować pliku objętego kontrolą źródła, który został zmodyfikowany.  
  
|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Zmodyfikuj plik tekstowy, który został wyewidencjonowany, sprawdź w pliku tylko (**Zaewidencjonuj** okno dialogowe)|1.  Utwórz nowy projekt za pomocą pliku tekstowego.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z i zmodyfikuj plik tekstowy.<br />4.  Sprawdź plik w folderze za pomocą okna dialogowego zaewidencjonowania (**pliku**, **kontroli źródła**, **Zaewidencjonuj**).|Typowe oczekiwane zachowanie.|  
|Zmodyfikuj plik tekstowy, który został wyewidencjonowany, sprawdź w pliku tylko (**oczekujące elementy do zaewidencjonowania** okna)|1.  Utwórz nowy projekt za pomocą pliku tekstowego.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z i zmodyfikuj plik tekstowy.<br />4.  Zaewidencjonuj za pośrednictwem **oczekujące elementy do zaewidencjonowania** okna.|Typowe oczekiwane zachowanie.|  
  
### <a name="case-4b-adding-files"></a>Zamierzone, Zapisz 4b: Dodawanie plików  
 Podczas dodawania pliku do projektu lub elementu do rozwiązania, projektu lub rozwiązania, należy również zmienić. Tym samym pliku nadrzędnego również jest wyewidencjonowany i muszą zostać zaewidencjonowane, aby zakończyć dodawanie.  
  
|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Dodaj plik tekstowy i zaewidencjonuj wszystko przed (**Zaewidencjonuj** okno dialogowe)|1.  Utwórz nowy projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj plik tekstowy do projektu.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowania projektu.<br />5.  Wybierz rozwiązanie w **Eksploratora rozwiązań**.<br />6.  Sprawdź **Zaewidencjonuj** okno dialogowe.|Typowe oczekiwane zachowanie.|  
|Dodaj plik tekstowy i zaewidencjonuj wszystko przed (**oczekujące elementy do zaewidencjonowania** okna)|1.  Utwórz nowy projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj plik tekstowy do projektu.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowania projektu.<br />5.  Zaewidencjonuj rozwiązanie z **oczekujące elementy do zaewidencjonowania** okna.|Typowe oczekiwane zachowanie.|  
  
### <a name="case-4c-adding-projects"></a>Zamierzone, Zapisz 4c: dodawanie projektów  
 Po dodaniu projektu do rozwiązania, należy także zmienić rozwiązania. Dlatego pliku rozwiązania jest wyewidencjonowany również i muszą zostać zaewidencjonowane, aby zakończyć dodawanie.  
  
|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Dodaj projekt do puste rozwiązanie pod kontrolą źródła (**Zaewidencjonuj** okno dialogowe)|1.  Utwórz puste rozwiązanie.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj nowy projekt.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowanie rozwiązania.<br />5.  Sprawdź **Zaewidencjonuj** okno dialogowe.|Typowe oczekiwane zachowanie.|  
|Dodaj projekt do puste rozwiązanie pod kontrolą źródła (**oczekujące elementy do zaewidencjonowania** okna)|1.  Utwórz puste rozwiązanie.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj nowy projekt.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowanie rozwiązania.<br />5.  Zaewidencjonuj rozwiązanie z **oczekujące elementy do zaewidencjonowania** okna.|Typowe oczekiwane zachowanie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

