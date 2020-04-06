---
title: Przewodnik po testach dla wtyczek kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6b3f8e76e977472a3459697a650b32dae657c22
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704376"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Przewodnik testowania wtyczek kontroli kodu źródłowego
Ta sekcja zawiera wskazówki dotyczące testowania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]wtyczki kontroli źródła za pomocą . Dostępny jest obszerny przegląd najczęstszych obszarów testowych, a także niektóre z bardziej skomplikowanych obszarów, które mogą być problematyczne. Ten przegląd nie ma być wyczerpującą listę przypadków testowych.

> [!NOTE]
> Niektóre poprawki błędów i ulepszenia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] najnowszego IDE mogą wykryć problemy z istniejącymi wtyczkami kontroli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]źródła, które wcześniej nie zostały napotkane podczas korzystania z poprzednich wersji programu . Zdecydowanie zaleca się przetestowanie istniejącej wtyczki kontroli źródła dla obszarów wyliczonych w tej sekcji, nawet jeśli nie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]wprowadzono żadnych zmian w uszczowcy od poprzedniej wersji programu .

## <a name="common-preparation"></a>Wspólny preparat
 Wymagana jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] maszyna z zainstalowaną wtyczką kontroli źródła docelowego i zainstalowana wtyczka kontroli źródła docelowego. Druga maszyna podobnie skonfigurowana może być używana dla niektórych testów kontroli open from source control.

## <a name="definition-of-terms"></a>Definicja terminów
 Do celów niniejszej przewodnika badawczego należy użyć następujących definicji terminów:

 Projekt klienta Dowolny typ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu dostępny w tym [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]obsługuje [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]integrację kontroli źródła (na przykład , , lub [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 Projekt sieci Web Istnieją cztery typy projektów sieci Web: system plików, lokalne usługi IIS, witryny zdalne i ftp.

- Projekty systemu plików są tworzone na ścieżce lokalnej, ale nie wymagają instalowania internetowych usług informacyjnych (IIS), ponieważ są dostępne wewnętrznie za pośrednictwem ścieżki UNC i mogą być umieszczane pod kontrolą źródła z wnętrza IDE, podobnie jak projekty klientów.

- Lokalne projekty IIS działają z iIS, który jest zainstalowany na tym samym komputerze i są dostępne z adresem URL wskazującym na komputerze lokalnym.

- Projekty lokacji zdalnych są również tworzone w ramach usług IIS, ale są one umieszczane pod kontrolą źródła na komputerze serwera usług IIS, a nie z wnętrza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- Projekty FTP są dostępne za pośrednictwem zdalnego serwera FTP, ale nie można ich umieścić pod kontrolą źródła.

  Rejestracja Inny termin dla rozwiązania lub projektu pod kontrolą źródła.

  Przechowywanie wersji Baza danych kontroli źródła, która jest dostępna za pośrednictwem interfejsu API wtyczki kontroli źródła.

## <a name="test-areas-covered-in-this-section"></a>Obszary testowe objęte niniejszą sekcją

- [Obszar testowy 1: Dodaj/Otwórz z kontroli źródła](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Przypadek 1a: Dodaj rozwiązanie do kontroli źródła

  - Przypadek 1b: Rozwiązanie otwarte z kontroli źródła

  - Przypadek 1c: Dodaj rozwiązanie z kontroli źródła

- [Obszar testowy 2: pobieranie z kontroli kodu źródłowego](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Obszar testu 3: Wyewidencjonuj/Cofnij wyewidencjonowanie](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Przypadek 3: Wyewidencjonuj/Cofnij wyewidencjonowanie

  - Przypadek 3a: Wyewidencjonuj

  - Przypadek 3b: Odłączony kasa

  - Przypadek 3c: Edycja kwerendy/Zapisywanie zapytań (QEQS)

  - Przypadek 3d: Cicha kasa

  - Przypadek 3e: Cofnij wyewidencjonowanie

- [Obszar testowy 4: zaewidencjonowanie](../../extensibility/internals/test-area-4-check-in.md)

  - Przypadek 4a: Zmodyfikowane przedmioty

  - Przypadek 4b: Dodawanie plików

  - Przypadek 4c: Dodawanie projektów

- [Obszar testowy 5: zmienianie kontroli kodu źródłowego](../../extensibility/internals/test-area-5-change-source-control.md)

  - Przypadek 5a: Bind

  - Przypadek 5b: Unbind

  - Przypadek 5c: Rebind

- [Obszar testowy 6: usuwanie](../../extensibility/internals/test-area-6-delete.md)

- [Obszar testowy 7: udostępnianie](../../extensibility/internals/test-area-7-share.md)

- [Obszar testowy 8: przełączanie wtyczki](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Przypadek 8a: Automatyczna zmiana

  - Przypadek 8b: Zmiana oparta na rozwiązaniu

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)
