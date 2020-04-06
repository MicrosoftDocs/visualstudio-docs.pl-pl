---
title: 'Obszar badania 4: Odprawa | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2386a217de228c5c47b467e6e083d978702927f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704572"
---
# <a name="test-area-4-check-in"></a>Obszar testowy 4: zaewidencjonowanie
Ten obszar testu wtyczki kontroli źródła obejmuje wysyłanie zaktualizowanych elementów do magazynu wersji za pomocą polecenia **Zaewidencjonuj.**

## <a name="command-menu-access"></a>Dostęp do menu polecenia
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ścieżki menu zintegrowanego środowiska programistycznego są używane w przypadkach testowych.

##### <a name="check-in"></a>Zamelduj się:
 **Plik**, **Kontrola źródła**, **Zaewidencjonuj**.

 **plik**, **Zaewidencjonuj**.

 Menu skrótów, **Zaewidencjonuj**.

## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie

- Projekty i pliki dodane do rozwiązania lub projektu pod kontrolą źródła są wyświetlane w oknie dialogowym **Zaewidencjonowywanie** i w oknie **Oczekujące zaewidencjonowania.**

- Po zaewidencjonowaniu dodane elementy są wyświetlane w formancie źródła.

- Po zaewidencjonowaniu zaktualizowane elementy są poprawnie wersjonetowane w sklepie.

## <a name="test-cases"></a>Przypadki testowe
 Poniżej przedstawiono konkretne przypadki testowe dla obszaru testowego Checkin.

### <a name="case-4a-modified-items"></a>Przypadek 4a: Zmodyfikowane przedmioty
 W tym artykule opisano użycie akcji zaewidencjonowania w celu zaktualizowania pliku pod kontrolą źródła, który został zmodyfikowany.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Modyfikowanie pliku tekstowego, który został wyewidencjonowany, tylko zaewidencjonuj plik (Okno dialogowe**Zaewidencjonuj)**|1. Utwórz nowy projekt z plikiem tekstowym.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Wyewidencjonuj i zmodyfikuj plik tekstowy.<br />4. Zaewidencjonuj za pomocą okna dialogowego Zaewidencjonuj **(Plik,** **Kontrola źródła,** **Zaewidencjonuj).**|Typowe oczekiwane zachowanie.|
|Modyfikowanie pliku tekstowego, który został wyewidencjonowany, tylko zaewidencjonuj plik **(okno Oczekujące zaewidencjonowania)**|1. Utwórz nowy projekt z plikiem tekstowym.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Wyewidencjonuj i zmodyfikuj plik tekstowy.<br />4. Zamelduj się za pomocą okna **Oczekujące odprawy.**|Typowe oczekiwane zachowanie.|

### <a name="case-4b-adding-files"></a>Przypadek 4b: Dodawanie plików
 Podczas dodawania pliku do projektu lub elementu do rozwiązania, projekt lub rozwiązanie musi również zmienić. W ten sposób plik nadrzędny jest również wyewidencjonowany i musi zostać zaewidencjonowany, aby zakończyć dodawanie.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Dodawanie pliku tekstowego i zaewidencjonowanie wszystkiego (Okno dialogowe**Zaewidencjonowywanie)**|1. Utwórz nowy projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj plik tekstowy do projektu.<br />4. Zaakceptuj wyewidencjonowanie projektu, jeśli zostanie wyświetlony monit.<br />5. Wybierz rozwiązanie w **Eksploratorze rozwiązań**.<br />6. Zaewidencjonuj w oknie dialogowym **Zaewidencjonuj.**|Typowe oczekiwane zachowanie.|
|Dodawanie pliku tekstowego i zaewidencjonowanie wszystkiego **(Okno Oczekujące zaewidencjonowanie)**|1. Utwórz nowy projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj plik tekstowy do projektu.<br />4. Zaakceptuj wyewidencjonowanie projektu, jeśli zostanie wyświetlony monit.<br />5. Zaewidencjonuj rozwiązanie z okna **Oczekujące zaewidencjonowania.**|Typowe oczekiwane zachowanie|

### <a name="case-4c-adding-projects"></a>Przypadek 4c: Dodawanie projektów
 Podczas dodawania projektu do rozwiązania rozwiązanie musi również ulec zmianie. W związku z tym plik rozwiązania jest również wyewidencjonowany i musi być zaewidencjonowany, aby zakończyć dodawanie.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Dodawanie projektu do pustego rozwiązania pod kontrolą źródła (Okno dialogowe**Zaewidencjonowywanie)**|1. Utwórz puste rozwiązanie.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj nowy projekt.<br />4. Zaakceptuj wyewidencjonowanie rozwiązania, jeśli zostanie wyświetlony monit.<br />5. Zaewidencjonuj w oknie dialogowym **Zaewidencjonuj.**|Typowe oczekiwane zachowanie.|
|Dodawanie projektu do pustego rozwiązania pod kontrolą źródła **(Okno Oczekujące zaewidencjonowania)**|1. Utwórz puste rozwiązanie.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj nowy projekt.<br />4. Zaakceptuj wyewidencjonowanie rozwiązania, jeśli zostanie wyświetlony monit.<br />5. Zaewidencjonuj rozwiązanie z okna **Oczekujące zaewidencjonowania.**|Typowe oczekiwane zachowanie.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
