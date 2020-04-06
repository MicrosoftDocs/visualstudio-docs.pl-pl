---
title: 'Obszar badania 2: Uzyskaj kontrolę nad źródłami | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c213e2774730596db8b8e4f2d0691472495222e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704604"
---
# <a name="test-area-2-get-from-source-control"></a>Obszar testowy 2: pobieranie z kontroli kodu źródłowego
Ten obszar testowy obejmuje przypadków testowych do pobierania elementów z magazynu wersji za pomocą polecenia Pobierz. Te przypadki testowe mogą być stosowane zarówno do projektów lokalnych, jak i do projektów sieci Web.

## <a name="command-menu-access"></a>Dostęp do menu polecenia
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ścieżki menu zintegrowanego środowiska programistycznego są używane w przypadkach testowych.

##### <a name="get-latest-version"></a>Pobierz najnowszą wersję:

- **Plik**, **Kontrola źródła**, **Pobierz najnowszą wersję**.

- **Plik**, **Pobierz najnowszą wersję**.

- Menu skrótów, **Pobierz najnowszą wersję**.

- Pobierz: **Plik**, **Kontrola źródła**, **Get**.

## <a name="expected-behavior"></a>Oczekiwane zachowanie

##### <a name="get-latest-version"></a>Pobierz najnowszą wersję:
 Wykonuje ciche (bez interfejsu użytkownika) pobieranie najnowszej wersji elementu z magazynu wersji.

##### <a name="get"></a>Pobierz:
 Wyświetla okno dialogowe **Pobierz** i umożliwia użytkownikowi wprowadzanie zmian w zestawie plików, które zostaną pobrane, a także modyfikowanie opcji, które mają wpływ na sposób pobierania plików.

## <a name="test-cases"></a>Przypadki testowe

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Pobierz najnowszą wersję pliku, który NIE istnieje lokalnie|1. Utwórz projekt.<br />2. Dodaj element do projektu.<br />3. Poddaj projekt kontroli źródła.<br />4. Usuń lokalną kopię towaru.<br />5. Pobierz najnowszą wersję elementu (menu skrótów, **Pobierz najnowszą wersję).**|Plik elementu jest pobierany lokalnie.|
|Pobierz plik, który NIE istnieje lokalnie|1. Utwórz projekt.<br />2. Dodaj element do projektu.<br />3. Poddaj projekt kontroli źródła.<br />4. Usuń lokalną kopię towaru.<br />5. Pobierz element **(Plik**, **Kontrola źródła**, **Pobierz** \<element>).|Plik elementu jest pobierany lokalnie.|
|Pobierz plik, który został wyewidencjonowany wyłącznie i zmodyfikowany lokalnie|1. Utwórz projekt.<br />2. Dodaj element do projektu.<br />3. Poddaj projekt kontroli źródła.<br />4. Sprawdź wyłącznie przedmiot projektu.<br />5. Zmodyfikuj kopię lokalną.<br />6. Pobierz najnowszą wersję elementu **(Plik**, **Pobierz najnowszą** \<wersję elementu>). Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />7. Kliknij przycisk **Zamień** w oknie dialogowym z ostrzeżeniem.|**ReResult z kroku 6**`:`<br /><br /> Okno dialogowe Ostrzeżenie wskazuje, że plik jest wyewidencjonowany.<br /><br /> **ReResult z kroku 7:**<br /><br /> Zmodyfikowany plik lokalny jest zastępowany przez oryginalną wersję ze sklepu wersji.<br /><br /> Plik jest odczytywany/zapisywany.|
|Pobierz i zamień plik, który jest wyewidencjonowany, udostępniony i zmodyfikowany lokalnie|1. Utwórz nowy projekt.<br />2. Dodaj element do projektu.<br />3. Poddaj projekt kontroli źródła.<br />4. Sprawdź element projektu jako udostępniony.<br />5. Zmodyfikuj kopię lokalną.<br />6. Pobierz najnowszą wersję elementu **(Plik**, **Pobierz najnowszą** \<wersję elementu>). Jeśli ten krok zakończy się pomyślnie, przejdź do następnego kroku.<br />7. Kliknij **przycisk Zamień** w oknie dialogowym z ostrzeżeniem.|**Wynik z kroku 6:**<br /><br /> Okno dialogowe Ostrzeżenie wskazuje, że plik jest wyewidencjonowany.<br /><br /> **Wynik z kroku 7:**<br /><br /> Zmodyfikowany plik lokalny jest zastępowany przez oryginalną wersję ze sklepu wersji.<br /><br /> Plik jest odczytywany/zapisywany.|
|Pobierz plik, który istnieje lokalnie, tak samo jak najnowsza wersja w magazynie wersji|1. Utwórz nowy projekt.<br />2. Dodaj element do projektu.<br />3. Poddaj projekt kontroli źródła.<br />4. Pobierz element **(Plik**, **Kontrola źródła**, **Pobierz** \<element>).|Plik lokalny pozostaje niezmieniony.|
|Uzyskaj rozwiązanie z jednym projektem|1. Utwórz rozwiązanie z jednym projektem.<br />2. Umieść rozwiązanie pod kontrolą źródła.<br />3. Usuń wszystkie pliki projektu lokalnie.<br />4. Pobierz rozwiązanie **(Plik**, **Kontrola źródła**, **Get**).|Wszystkie usunięte pliki są przywracane lokalnie.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
