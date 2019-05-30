---
title: 'Obszar testowy 7: Udostępnij | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b117bcf78d4644533f8931296e6f726281fe14e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327846"
---
# <a name="test-area-7-share"></a>Obszar testowy 7: Udostępnij
Obszar ten test obejmuje udostępniania elementów między lokalizacjami za pośrednictwem **udziału** polecenia.

 Operacja hhare jest oczywisty duplikatów plików i folderów elementów między co najmniej dwóch lokalizacjach w ramach hierarchii plików w kontroli źródła. Duplikowanie nie naprawdę odbywa się na serwerze, ale użytkownik widzi tego samego pliku, w dwóch lub więcej określonych lokalizacjach. Zawsze, gdy zmiany zostaną wprowadzone do wszystkich elementów udostępnionych, te zmiany są widoczne we wszystkich lokalizacjach udostępnionych.

 Udostępnianie do folderów, które działa, jeśli został wskazany folder z co najmniej jeden plik pod kontrolą źródła w nim. Polecenie udziału jest wyłączone w następujących warunkach:

- Jeśli wybrany folder jest pusty folder.

- Jeśli istnieje folder rzeczywistych, ale nie zawiera on nie plików do kontroli źródła.

- Jeśli istnieje folder wirtualny, czy pliki objęte kontrolą źródła są w nim, czy nie.

- W przypadku projektu zdalnej witryny sieci Web.

## <a name="command-menu-access"></a>Dostęp do Menu polecenia
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ścieżki menu środowiska zintegrowanego rozwoju są używane w przypadkach testowych.

 Udostępnij: **Plik**->**kontroli źródła**->**udziału**.

## <a name="expected-behavior"></a>Oczekiwane zachowanie

- Udostępniony plik pojawia się w lokalizacji udostępnionej.

- Wyświetlanie źródła kontrolka wersji magazynu historii pokaże udostępniane pliki.

- Edytowanie pliku udostępnionego edytuje zarówno w lokalizacji pliku.

## <a name="test-cases"></a>Przypadki testowe
 Poniżej przedstawiono określonych przypadków testowych dla obszaru testu udziału.

|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|
|------------|----------------|--------------------------------|
|Udostępnianie pliku z jednego załadowanego projektu objętego kontrolą źródła w innym załadowanego projektu|1.  Utwórz nowy projekt.<br />2.  Dodaj drugi projekt do rozwiązania.<br />3.  Utwórz plik w drugi projekt o nazwie, która nie znajduje się w pierwszy projekt.<br />4.  Dodaj rozwiązanie do kontroli źródła.<br />5.  Wybierz pierwszy projekt.<br />6.  Otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />7.  Udostępnij plik z projektu drugiego do pierwszego projektu.<br />8.  Zaakceptuj **Wyewidencjonuj** Jeśli zostanie wyświetlony monit.|Typowe oczekiwane zachowanie.|
|Udostępnianie plików z jednego projektu do innego|1.  Utwórz nowy projekt.<br />2.  Dodaj go do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Utwórz drugi projekt (nowe rozwiązanie).<br />5.  Dodaj rozwiązanie do kontroli źródła.<br />6.  Wybierz projekt.<br />7.  Otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />8.  Udostępnij plik z projektu uprzednio dodanych do otwartego projektu.<br />9. Zaakceptuj **Wyewidencjonuj** Jeśli zostanie wyświetlony monit.|Typowe oczekiwane zachowanie.|
|Udostępnianie pliku nie jest częścią projektu z kontroli źródła w aktualnie załadowanych projektów|1.  Utwórz nowy projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj plik do kontroli źródła, który nie jest częścią projektu lub rozwiązania.<br />4.  Wybierz projekt, a następnie otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />5.  Wybierz plik, w ramach **udostępnianie** okno dialogowe, które nie istnieje w bieżącym projekcie lub rozwiązaniu i udostępnić go.<br />6.  Zaakceptuj **Wyewidencjonuj** Jeśli zostanie wyświetlony monit.|Magazynu kontroli źró przeprowadził Get, więc plik jest teraz w lokalizacji lokalnej projektu.|
|Udostępnianie plików w ramach tego samego projektu do innego folderu|1.  Wybierz **Wyewidencjonuj automatycznie** w **narzędzia** -> **opcje** -> **kontroli źródła**.<br />2.  Utwórz nowy projekt i dodaj go do kontroli źródła.<br />3.  Dodaj folder do projektu.<br />4.  Dodaj plik do folderu, a następnie sprawdź w folderze.<br />5.  Wybierz folder.<br />6.  Otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />7.  Udostępnij plik do wybranego folderu.|Typowe oczekiwane zachowanie.<br /><br /> Folder muszą zostać sprawdzone za pomocą pliku w nim, zanim będzie można używać dla udziału.|
|Udostępnij folder do załadowanego projektu — cykliczna|1.  Utwórz nowy projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Wybierz projekt.<br />4.  Otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />5.  Wybierz folder.<br />6.  Udostępnij rekursywnie folderu do projektu.|Typowe oczekiwane zachowanie.|
|Udostępnianie kilka plików z jednego projektu do innego|1.  Utwórz nowy projekt z kilku plików w nim.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Tworzenie nowego projektu w nowym rozwiązaniu.<br />5.  Dodaj rozwiązanie do kontroli źródła.<br />6.  Wybierz projekt.<br />7.  Otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />8.  Udostępnij kilka plików z wcześniej utworzonym projektem aktualnie otwartym projekcie.|Typowe oczekiwane zachowanie.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)