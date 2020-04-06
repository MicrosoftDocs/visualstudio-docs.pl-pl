---
title: 'Obszar badania 7: Udział | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd4c48e94015d95f5e56d465cdbf98562108d3b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704406"
---
# <a name="test-area-7-share"></a>Obszar testowy 7: udostępnianie
Ten obszar testowy obejmuje udostępnianie elementów między lokalizacjami za pomocą polecenia **Udostępnij.**

 Operacja hhare jest widoczne powielanie plików i elementów folderów między dwoma lub więcej lokalizacji w hierarchii plików kontroli źródła. Duplikacja nie występuje na serwerze, ale użytkownik widzi ten sam plik w dwóch lub więcej określonych lokalizacjach. Za każdym razem, gdy wprowadzane są zmiany w dowolnym z elementów udostępnionych, zmiany te są wyświetlane we wszystkich innych lokalizacjach udostępnionych.

 Udostępnianie w folderach działa, jeśli wybierzesz folder z co najmniej jednym plikiem pod kontrolą źródła. Polecenie share jest wyłączone pod następującymi warunkami:

- Jeśli wybrany folder jest pustym folderem.

- Jeśli istnieje prawdziwy folder, ale nie zawiera żadnych plików kontroli źródła.

- Jeśli istnieje folder wirtualny, czy pliki pod kontrolą źródła znajdują się w nim, czy nie.

- Jeśli istnieje projekt witryny zdalnej w sieci Web.

## <a name="command-menu-access"></a>Dostęp do menu polecenia
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ścieżki menu zintegrowanego środowiska programistycznego są używane w przypadkach testowych.

 Udostępnij:**Udział****kontroli**->źródła **plików**->.

## <a name="expected-behavior"></a>Oczekiwane zachowanie

- Udostępniony plik jest wyświetlany w lokalizacji udostępnionej.

- Wyświetlanie historii magazynu wersji kontroli źródła pokazuje, że pliki są udostępniane.

- Edycja udostępnionego pliku edytuje obie lokalizacje pliku.

## <a name="test-cases"></a>Przypadki testowe
 Poniżej przedstawiono konkretne przypadki testowe dla obszaru testu udostępnić.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Udostępnianie pliku z jednego załadowanego projektu pod kontrolą źródła do innego załadowanego projektu|1. Utwórz nowy projekt.<br />2. Dodaj drugi projekt do rozwiązania.<br />3. Utwórz plik w drugim projekcie o nazwie, która nie znajduje się w pierwszym projekcie.<br />4. Dodaj rozwiązanie do kontroli źródła.<br />5. Wybierz pierwszy projekt.<br />6. Otwórz okno dialogowe **Udostępnianie** **(Udział****kontroli** -> źródła**pliku).** -> <br />7. Udostępnij plik z drugiego projektu do pierwszego projektu.<br />8. Zaakceptuj **wyewidencjonowanie,** jeśli zostanie wyświetlony monit.|Typowe oczekiwane zachowanie.|
|Udostępnianie pliku z jednego projektu do drugiego|1. Utwórz nowy projekt.<br />2. Dodaj go do kontroli źródła.<br />3. Zamknąć roztwór.<br />4. Utwórz drugi projekt (nowe rozwiązanie).<br />5. Dodaj rozwiązanie do kontroli źródła.<br />6. Wybierz projekt.<br />7. Otwórz okno dialogowe **Udostępnianie** **(Udział****kontroli** -> źródła**pliku).** -> <br />8. Udostępnij plik z wcześniej dodanego projektu do otwartego projektu.<br />9. Zaakceptuj **wyewidencjonowanie,** jeśli zostanie wyświetlony monit.|Typowe oczekiwane zachowanie.|
|Udostępnianie pliku niewchodzącego w skład projektu z kontroli źródła w aktualnie załadowanym projekcie|1. Utwórz nowy projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj plik do kontroli źródła, który nie jest częścią projektu lub rozwiązania.<br />4. Wybierz projekt i otwórz okno dialogowe **Udostępnianie** **(Udział****w kontroli** -> źródła**plików).** -> <br />5. Wybierz plik w oknie dialogowym **Udostępnianie,** który nie istnieje w bieżącym projekcie lub rozwiązaniu i udostępnij go.<br />6. Zaakceptuj **wyewidencjonowanie,** jeśli zostanie wyświetlony monit.|Magazyn kontroli źródła wykonał Get, więc plik jest teraz w lokalnej lokalizacji projektu.|
|Udostępnianie plików w ramach tego samego projektu do innego folderu|1. Wybierz opcję **Wyewidencjonuj automatycznie** w obszarze**Opcje** ->  **narzędzi.** -> **Source Control**<br />2. Utwórz nowy projekt i dodaj go do kontroli źródła.<br />3. Dodaj folder do projektu.<br />4. Dodaj plik do folderu i zaewidencjonuj folder.<br />5. Wybierz folder.<br />6. Otwórz okno dialogowe **Udostępnianie** **(Udział****kontroli** -> źródła**pliku).** -> <br />7. Udostępnij plik do wybranego folderu.|Typowe oczekiwane zachowanie.<br /><br /> Folder musi zostać zaewidencjonowany z plikiem w nim, zanim będzie można go użyć do udostępnienia.|
|Udostępnianie folderu w załadowanym projekcie — cykliczne|1. Utwórz nowy projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Wybierz projekt.<br />4. Otwórz okno dialogowe **Udostępnianie** **(Udział****kontroli** -> źródła**pliku).** -> <br />5. Wybierz folder.<br />6. Udostępnij folder rekursywnie w projekcie.|Typowe oczekiwane zachowanie.|
|Udostępnianie kilku plików z jednego projektu do drugiego|1. Utwórz nowy projekt z kilkoma plikami.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Zamknąć roztwór.<br />4. Utwórz nowy projekt w nowym rozwiązaniu.<br />5. Dodaj rozwiązanie do kontroli źródła.<br />6. Wybierz projekt.<br />7. Otwórz okno dialogowe **Udostępnianie** **(Udział****kontroli** -> źródła**pliku).** -> <br />8. Udostępnij kilka plików z poprzednio utworzonego projektu do aktualnie otwartego projektu.|Typowe oczekiwane zachowanie.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
