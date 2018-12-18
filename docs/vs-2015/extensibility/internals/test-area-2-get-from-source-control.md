---
title: 'Obszar testowy 2: Pobieranie z kontroli źródła | Dokumentacja firmy Microsoft'
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
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96b00cfc9965b6006fa51b3cd313566658d604bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786161"
---
# <a name="test-area-2-get-from-source-control"></a>Obszar testowy 2: pobieranie z kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Obszar ten test obejmuje przypadki testowe do pobierania elementów z magazynu w wersji za pomocą polecenia Get. Te przypadki testowe można zastosować do lokalnego i projektów sieci Web.  
  
## <a name="command-menu-access"></a>Dostęp do Menu polecenia  
 Następujące [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ścieżki menu środowiska zintegrowanego rozwoju są używane w przypadkach testowych.  
  
##### <a name="get-latest-version"></a>Pobierz najnowszą wersję:  
  
-   **Plik**, **kontroli źródła**, **Pobierz najnowszą wersję**.  
  
-   **Plik**, **Pobierz najnowszą wersję**.  
  
-   Menu skrótów **Pobierz najnowszą wersję**.  
  
-   Pobierz: **pliku**, **kontroli źródła**, **uzyskać**.  
  
## <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
##### <a name="get-latest-version"></a>Pobierz najnowszą wersję:  
 Wykonuje pobierania silent (nie interfejsu użytkownika) w najnowszej wersji elementu z magazynu wersji.  
  
##### <a name="get"></a>Pobierz:  
 Wyświetla **uzyskać** okno dialogowe i umożliwia użytkownikowi wprowadzić zmiany do zestawu plików, który zostanie pobrany, a także zmodyfikować opcje, które wpływają na sposób pliki są pobierane.  
  
## <a name="test-cases"></a>Przypadki testowe  
  
|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Pobierz najnowszą wersję pliku, który nie istnieje lokalnie|1.  Utwórz projekt.<br />2.  Dodaj element do projektu.<br />3.  Umieść projektu objętego kontrolą źródła.<br />4.  Usuń lokalną kopię elementu.<br />5.  Pobierz najnowszą wersję elementu (Menu skrótów **Pobierz najnowszą wersję**).|Plik elementu jest pobierana lokalnie.|  
|Pobierz plik, który nie istnieje lokalnie|1.  Utwórz projekt.<br />2.  Dodaj element do projektu.<br />3.  Umieść projektu objętego kontrolą źródła.<br />4.  Usuń lokalną kopię elementu.<br />5.  Pobierz element (**pliku**, **kontroli źródła**, **uzyskać** \<element >).|Plik elementu jest pobierana lokalnie.|  
|Pobieranie pliku, który został wyewidencjonowany w trybie wyłączności i zmodyfikowany lokalnie|1.  Utwórz projekt.<br />2.  Dodaj element do projektu.<br />3.  Umieść projektu objętego kontrolą źródła.<br />4.  Zapoznaj się z elementu projektu wyłącznie.<br />5.  Modyfikowanie kopii lokalnej.<br />6.  Pobierz najnowszą wersję elementu (**pliku**, **Pobierz najnowszą wersję** \<element >). Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />7.  Kliknij przycisk **Zastąp** przycisku w oknie dialogowym ostrzeżenia.|**ReResult w kroku 6** `:`<br /><br /> Okno dialogowe ostrzeżenia wskazuje, że ten plik został wyewidencjonowany.<br /><br /> **ReResult w kroku 7:**<br /><br /> Zmodyfikowany plik lokalny zastępuje oryginalną wersję z magazynu wersji.<br /><br /> Plik jest odczytu/zapisu.|  
|Pobierz i zastąpić plik, który jest wyewidencjonowany, udostępniony i zmodyfikowany lokalnie|1.  Utwórz nowy projekt.<br />2.  Dodaj element do projektu.<br />3.  Umieść projektu objętego kontrolą źródła.<br />4.  Zapoznaj się z elementu projektu jako udostępniony.<br />5.  Modyfikowanie kopii lokalnej.<br />6.  Pobierz najnowszą wersję elementu (**pliku**, **Pobierz najnowszą wersję** \<element >). Jeśli ta czynność zakończy się powodzeniem, przejdź do następnego kroku.<br />7.  Kliknij przycisk **Zastąp** w oknie dialogowym ostrzeżenia.|**Wynikiem krok 6:**<br /><br /> Okno dialogowe ostrzeżenia wskazuje, że ten plik został wyewidencjonowany.<br /><br /> **Wynikiem kroku 7:**<br /><br /> Zmodyfikowany plik lokalny zastępuje oryginalną wersję z magazynu wersji.<br /><br /> Plik jest odczytu/zapisu.|  
|Pobierz plik, który istnieje lokalnie w taki sam jak najnowszej wersji usługi magazynu w wersji|1.  Utwórz nowy projekt.<br />2.  Dodaj element do projektu.<br />3.  Umieść projektu objętego kontrolą źródła.<br />4.  Pobierz element (**pliku**, **kontroli źródła**, **uzyskać** \<element >).|Lokalny plik pozostaje bez zmian.|  
|Rozwiązanie z jednym projektem|1.  Tworzenie rozwiązań za pomocą jednego projektu.<br />2.  Umieść rozwiązanie pod kontrolą źródła.<br />3.  Usuń wszystkie pliki projektu lokalnie.<br />4.  Pobieranie rozwiązania (**pliku**, **kontroli źródła**, **uzyskać**).|Wszystkie usunięte pliki zostaną przywrócone lokalnie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

