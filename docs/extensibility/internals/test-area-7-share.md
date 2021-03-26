---
title: 'Obszar testowy 7: udostępnianie | Microsoft Docs'
description: Ten obszar testowania kontroli źródła obejmuje udostępnianie elementów między lokalizacjami przy użyciu polecenia udostępniania dla wtyczki kontroli źródła programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: facfb48fbe02ff374c594f1ddadf0710c1f989d6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074356"
---
# <a name="test-area-7-share"></a>Obszar testowy 7: Udostępnij
Ten obszar testowy obejmuje udostępnianie elementów między lokalizacjami za pośrednictwem polecenia **udostępniania** .

 Operacja hhare to widoczne duplikowanie plików i elementów folderów między dwiema lub większą liczbą lokalizacji w hierarchii plików kontroli źródła. Duplikowanie nie występuje na serwerze, ale użytkownik widzi ten sam plik w co najmniej dwóch określonych lokalizacjach. Po wprowadzeniu zmian do któregokolwiek z elementów udostępnionych te zmiany są wyświetlane we wszystkich innych udostępnionych lokalizacjach.

 Udostępnianie w folderach działa w przypadku wybrania folderu z co najmniej jednym plikiem pod kontrolą źródła. Polecenie Share jest wyłączone w następujących warunkach:

- Jeśli wybrany folder jest pustym folderem.

- Jeśli istnieje rzeczywisty folder, ale nie zawiera on plików kontroli źródła.

- Jeśli istnieje folder wirtualny, niezależnie od tego, czy pliki pod kontrolą źródła znajdują się w nim.

- Jeśli istnieje zdalny projekt sieci Web.

## <a name="command-menu-access"></a>Dostęp do menu poleceń
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]W przypadku przypadków testowych używane są następujące ścieżki menu zintegrowanego środowiska deweloperskiego.

 Udostępnianie:  -> **udział kontroli źródła** plików -> .

## <a name="expected-behavior"></a>Oczekiwane zachowanie

- Udostępniony plik jest wyświetlany w lokalizacji udostępnionej.

- Wyświetlanie historii magazynu wersji kontroli źródła pokazuje, że pliki są udostępnione.

- Edytowanie udostępnionego pliku umożliwia edycję obu lokalizacji pliku.

## <a name="test-cases"></a>Przypadki testowe
 Następujące przypadki testowe są określone dla obszaru testowego udostępniania.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Udostępnianie pliku z jednego załadowanego projektu pod kontrolą źródła do innego załadowanego projektu|1. Utwórz nowy projekt.<br />2. Dodaj drugi projekt do rozwiązania.<br />3. Utwórz plik w drugim projekcie z nazwą, która nie znajduje się w pierwszym projekcie.<br />4. Dodaj rozwiązanie do kontroli źródła.<br />5. Wybierz pierwszy projekt.<br />6. Otwórz okno dialogowe **udostępniania** (  ->  **udział kontroli źródła** plików  ->  ).<br />7. Udostępnij plik z drugiego projektu do pierwszego projektu.<br />8 **. Zaakceptuj** wyewidencjonowanie, jeśli zostanie wyświetlony monit.|Typowe oczekiwane zachowanie.|
|Udostępnianie pliku z jednego projektu do innego|1. Utwórz nowy projekt.<br />2. Dodaj ją do kontroli źródła.<br />3. Zamknij rozwiązanie.<br />4. Utwórz drugi projekt (nowe rozwiązanie).<br />5. Dodaj rozwiązanie do kontroli źródła.<br />6. Wybierz projekt.<br />7. Otwórz okno dialogowe **udostępnianie** (  ->  **udział kontroli źródła** plików  ->  ).<br />8. Udostępnij plik z wcześniej dodanego projektu do otwartego projektu.<br />9 **. Zaakceptuj** wyewidencjonowanie, jeśli zostanie wyświetlony monit.|Typowe oczekiwane zachowanie.|
|Udostępnianie pliku nienależącego do projektu z kontroli źródła do aktualnie załadowanego projektu|1. Utwórz nowy projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj plik do kontroli źródła, która nie jest częścią projektu lub rozwiązania.<br />4. Wybierz projekt i Otwórz okno dialogowe **udostępnianie** (  ->  **udział kontroli źródła** plików  ->  ).<br />5. Wybierz plik w oknie dialogowym **udział** , który nie istnieje w bieżącym projekcie lub rozwiązaniu i udostępnij go.<br />6 **. Zaakceptuj** wyewidencjonowanie, jeśli zostanie wyświetlony monit.|Magazyn kontroli źródła wykonał pobieranie, więc plik znajduje się teraz w lokalizacji lokalnej projektu.|
|Udostępnianie plików w tym samym projekcie do innego folderu|1. Wybierz pozycję **Wyewidencjonuj automatycznie** w obszarze **Narzędzia**  ->  **Opcje**  ->  **kontroli źródła**.<br />2. Utwórz nowy projekt i dodaj go do kontroli źródła.<br />3. Dodaj folder do projektu.<br />4. Dodaj plik do folderu i Zaewidencjonuj go.<br />5. Wybierz folder.<br />6. Otwórz okno dialogowe **udostępniania** (  ->  **udział kontroli źródła** plików  ->  ).<br />7. Udostępnij plik w wybranym folderze.|Typowe oczekiwane zachowanie.<br /><br /> Folder musi być zaewidencjonowany przy użyciu pliku, zanim będzie można go użyć do udostępniania.|
|Udostępnianie folderu w załadowanym projekcie — rekursywnie|1. Utwórz nowy projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Wybierz projekt.<br />4. Otwórz okno dialogowe **udostępnianie** (  ->  **udział kontroli źródła** plików  ->  ).<br />5. Wybierz folder.<br />6. Udostępnij folder rekursywnie w projekcie.|Typowe oczekiwane zachowanie.|
|Udostępnianie kilku plików z jednego projektu do innego|1. Utwórz nowy projekt zawierający kilka plików.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Zamknij rozwiązanie.<br />4. Utwórz nowy projekt w nowym rozwiązaniu.<br />5. Dodaj rozwiązanie do kontroli źródła.<br />6. Wybierz projekt.<br />7. Otwórz okno dialogowe **udostępnianie** (  ->  **udział kontroli źródła** plików  ->  ).<br />8. Udostępnij w aktualnie otwartym projekcie kilka plików z wcześniej utworzonego projektu.|Typowe oczekiwane zachowanie.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
