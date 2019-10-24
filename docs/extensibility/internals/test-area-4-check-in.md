---
title: 'Obszar testowy 4: Zaewidencjonuj | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9144bf3aa677a2478bce81634d22d6446e77626b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722523"
---
# <a name="test-area-4-check-in"></a>Obszar testowy 4: zaewidencjonowanie
Ten obszar testowania wtyczki kontroli źródła obejmuje wysyłanie zaktualizowanych elementów do magazynu wersji za pomocą polecenia **Zaewidencjonuj** .

## <a name="command-menu-access"></a>Dostęp do menu poleceń
 W przypadku przypadków testowych używane są [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] następujące ścieżki menu zintegrowanego środowiska deweloperskiego.

##### <a name="check-in"></a>Zamelduj się:
 **Plik**, **Kontrola źródła**, **ewidencjonowanie**.

 **Plik**, **Zaewidencjonuj**.

 Menu skrótów, **Zaewidencjonuj**.

## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie

- Projekty i pliki dodane do rozwiązania lub projektu pod kontrolą źródła są wyświetlane w oknie dialogowym **ewidencjonowanie** i w oknie **Oczekujące zaewidencjonowania** .

- Po zaewidencjonowaniu dodane elementy są wyświetlane w kontroli źródła.

- Po zaewidencjonowaniu zaktualizowane elementy są prawidłowo zgodne z wersją w sklepie.

## <a name="test-cases"></a>Przypadki testowe
 Poniższe przypadki testowe dotyczą obszaru testowego zaewidencjonowania.

### <a name="case-4a-modified-items"></a>Przypadek 4a: zmodyfikowane elementy
 Opisuje użycie akcji zaewidencjonowania w celu zaktualizowania pliku w ramach kontroli źródła, który został zmodyfikowany.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Modyfikuj plik tekstowy, który został wyewidencjonowany, Zaewidencjonuj tylko plik (okno dialogowe**Zaewidencjonuj** )|1. Utwórz nowy projekt z plikiem tekstowym.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Wyewidencjonuj i zmodyfikuj plik tekstowy.<br />4. Zaewidencjonuj przy użyciu okna dialogowego ewidencjonowanie (**plik**, **Kontrola źródła**, **ewidencjonowanie**).|Typowe oczekiwane zachowanie.|
|Zmodyfikuj plik tekstowy, który został wyewidencjonowany, Zaewidencjonuj tylko plik (**oczekujące okno zaewidencjonowania** )|1. Utwórz nowy projekt z plikiem tekstowym.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Wyewidencjonuj i zmodyfikuj plik tekstowy.<br />4. Zaewidencjonuj przy użyciu okna **Oczekujące zaewidencjonowania** .|Typowe oczekiwane zachowanie.|

### <a name="case-4b-adding-files"></a>Przypadek 4B: Dodawanie plików
 Podczas dodawania pliku do projektu lub elementu do rozwiązania, należy również zmienić projekt lub rozwiązanie. W rezultacie plik nadrzędny jest również wyewidencjonowany i musi być zaewidencjonowany, aby ukończyć Dodawanie.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Dodaj plik tekstowy i Zaewidencjonuj wszystko (**Zaewidencjonuj** )|1. Utwórz nowy projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj plik tekstowy do projektu.<br />4. Zaakceptuj wyewidencjonowanie projektu, jeśli zostanie wyświetlony monit.<br />5. Wybierz rozwiązanie w **Eksplorator rozwiązań**.<br />6. Zaewidencjonuj z okna dialogowego **Zaewidencjonuj** .|Typowe oczekiwane zachowanie.|
|Dodaj plik tekstowy i Zaewidencjonuj wszystko (**oczekujące okno zaewidencjonowania** )|1. Utwórz nowy projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj plik tekstowy do projektu.<br />4. Zaakceptuj wyewidencjonowanie projektu, jeśli zostanie wyświetlony monit.<br />5. Sprawdź rozwiązanie w oknie **Oczekujące zaewidencjonowania** .|Typowe oczekiwane zachowanie|

### <a name="case-4c-adding-projects"></a>Przypadek 4C: Dodawanie projektów
 W przypadku dodawania projektu do rozwiązania, rozwiązanie musi być również zmienione. W ten sposób plik rozwiązania jest również wyewidencjonowany i należy go zaewidencjonować, aby ukończyć Dodawanie.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Dodaj projekt do pustego rozwiązania w obszarze kontroli źródła (okno dialogowe**ewidencjonowanie** )|1. Utwórz puste rozwiązanie.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj nowy projekt.<br />4. Zaakceptuj Wyewidencjonuj rozwiązanie, jeśli zostanie wyświetlony monit.<br />5. Zaewidencjonuj z okna dialogowego **Zaewidencjonuj** .|Typowe oczekiwane zachowanie.|
|Dodaj projekt do pustego rozwiązania w obszarze kontroli źródła (okno**oczekujące na zaewidencjonowania** )|1. Utwórz puste rozwiązanie.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj nowy projekt.<br />4. Zaakceptuj Wyewidencjonuj rozwiązanie, jeśli zostanie wyświetlony monit.<br />5. Sprawdź rozwiązanie w oknie **Oczekujące zaewidencjonowania** .|Typowe oczekiwane zachowanie.|

## <a name="see-also"></a>Zobacz także
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)