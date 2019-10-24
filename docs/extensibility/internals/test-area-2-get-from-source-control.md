---
title: 'Obszar testowy 2: pobieranie z kontroli źródła | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca98c927209062d2a1fc67c309d2f32c18d1b5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722571"
---
# <a name="test-area-2-get-from-source-control"></a>Obszar testowy 2: pobieranie z kontroli kodu źródłowego
Ten obszar testowy obejmuje przypadki testowe związane z pobieraniem elementów z magazynu wersji za pomocą polecenia Get. Te przypadki testowe mogą być stosowane zarówno do projektów lokalnych, jak i w sieci Web.

## <a name="command-menu-access"></a>Dostęp do menu poleceń
 W przypadku przypadków testowych używane są [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] następujące ścieżki menu zintegrowanego środowiska deweloperskiego.

##### <a name="get-latest-version"></a>Pobierz najnowszą wersję:

- **Plik**, **Kontrola źródła**, **pobieranie najnowszej wersji**.

- **Pobierz najnowszą wersję** **pliku**.

- Menu skrótów, **Pobierz najnowszą wersję**.

- Pobieranie: **plik**, **Kontrola źródła**, **pobieranie**.

## <a name="expected-behavior"></a>Oczekiwane zachowanie

##### <a name="get-latest-version"></a>Pobierz najnowszą wersję:
 Wykonuje ciche (bez interfejsu użytkownika) pobieranie najnowszej wersji elementu z magazynu wersji.

##### <a name="get"></a>Pobierz:
 Wyświetla okno dialogowe **pobieranie** i umożliwia użytkownikowi wprowadzanie zmian w zestawie plików, który zostanie pobrany, oraz modyfikowanie opcji, które mają wpływ na sposób pobierania plików.

## <a name="test-cases"></a>Przypadki testowe

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Pobierz najnowszą wersję pliku, który nie istnieje lokalnie|1. Utwórz projekt.<br />2. Dodaj element do projektu.<br />3. Umieść projekt pod kontrolą źródła.<br />4. Usuń lokalną kopię elementu.<br />5. Pobierz najnowszą wersję elementu (menu skrótów, **Pobierz najnowszą wersję**).|Plik elementu jest pobierany lokalnie.|
|Pobierz plik, który nie istnieje lokalnie|1. Utwórz projekt.<br />2. Dodaj element do projektu.<br />3. Umieść projekt pod kontrolą źródła.<br />4. Usuń lokalną kopię elementu.<br />5. Pobierz element (**plik**, **Kontrola źródła**, **Pobierz** \<item >).|Plik elementu jest pobierany lokalnie.|
|Pobierz plik, który został wyewidencjonowany na wyłączność i zmodyfikowany lokalnie|1. Utwórz projekt.<br />2. Dodaj element do projektu.<br />3. Umieść projekt pod kontrolą źródła.<br />4. Wyewidencjonuj element projektu w trybie wyłączności.<br />5. Zmodyfikuj kopię lokalną.<br />6. Pobierz najnowszą wersję elementu (**plik**, **pobierz najnowszą wersję** \<item >). Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />7. kliknij przycisk **Zamień** w oknie dialogowym ostrzeżenia.|**Wynik z kroku 6** `:`<br /><br /> Okno dialogowe ostrzeżenia wskazuje, że plik jest wyewidencjonowany.<br /><br /> **Wynik z kroku 7:**<br /><br /> Zmodyfikowany plik lokalny jest zastępowany przez oryginalną wersję z magazynu wersji.<br /><br /> Plik jest do odczytu/zapisu.|
|Pobierz i Zamień plik, który jest wyewidencjonowany, udostępniony i zmodyfikowany lokalnie|1. Utwórz nowy projekt.<br />2. Dodaj element do projektu.<br />3. Umieść projekt pod kontrolą źródła.<br />4. Sprawdź element projektu jako udostępniony.<br />5. Zmodyfikuj kopię lokalną.<br />6. Pobierz najnowszą wersję elementu (**plik**, **pobierz najnowszą wersję** \<item >). Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />7. kliknij pozycję **Zamień** w oknie dialogowym ostrzeżenia.|**Wynik z kroku 6:**<br /><br /> Okno dialogowe ostrzeżenia wskazuje, że plik jest wyewidencjonowany.<br /><br /> **Wynik z kroku 7:**<br /><br /> Zmodyfikowany plik lokalny jest zastępowany przez oryginalną wersję z magazynu wersji.<br /><br /> Plik jest do odczytu/zapisu.|
|Pobierz plik, który istnieje lokalnie, tak samo jak Najnowsza wersja w sklepie z wersjami|1. Utwórz nowy projekt.<br />2. Dodaj element do projektu.<br />3. Umieść projekt pod kontrolą źródła.<br />4. Pobierz element (**plik**, **Kontrola źródła**, **Pobierz** \<item >).|Plik lokalny jest niezmieniony.|
|Uzyskaj rozwiązanie z jednym projektem|1. Utwórz rozwiązanie z jednym projektem.<br />2. Umieść rozwiązanie pod kontrolą źródła.<br />3. Usuń wszystkie pliki projektu lokalnie.<br />4. Pobierz rozwiązanie (**plik**, **Kontrola źródła**, **Pobierz**).|Wszystkie usunięte pliki zostaną przywrócone lokalnie.|

## <a name="see-also"></a>Zobacz także
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)