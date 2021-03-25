---
title: Przewodnik testowy dla wtyczek kontroli źródła | Microsoft Docs
description: Dowiedz się więcej na temat testowania wtyczki kontroli źródła w programie Visual Studio. To omówienie obejmuje typowe obszary testowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 465378069c5ac5d5a516e94bdaa2120a843d9914
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090788"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Przewodnik testowania wtyczek kontroli kodu źródłowego
Ta sekcja zawiera wskazówki dotyczące testowania wtyczki kontroli źródła za pomocą programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Jest to obszerne omówienie najpopularniejszych obszarów testowania, a także niektóre bardziej Intricate obszary, które mogą być problematyczne. Tego omówienia nie jest to pełna lista przypadków testowych.

> [!NOTE]
> Niektóre poprawki błędów i ulepszenia najnowszego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska IDE mogą odkrywać problemy z istniejącymi wtyczkami kontroli źródła, które wcześniej nie były używane podczas korzystania z poprzednich wersji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Zdecydowanie zaleca się przetestowanie istniejącej wtyczki kontroli źródła dla obszarów wyliczanych w tej sekcji, nawet jeśli nie wprowadzono żadnych zmian do wtyczki od czasu poprzedniej wersji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="common-preparation"></a>Wspólne przygotowanie
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Wymagana jest maszyna z i docelowa wtyczka do kontroli źródła. Druga skonfigurowana konfiguracja może być używana w przypadku niektórych otwartych z testów kontroli źródła.

## <a name="definition-of-terms"></a>Definicja warunków
 Na potrzeby tego przewodnika testowego należy użyć następujących definicji warunku:

 Projekt klienta dowolny typ projektu dostępny w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługujący integrację kontroli źródła (na przykład,, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ).

 Projekt sieci Web zawiera cztery typy projektów sieci Web: system plików, lokalne usługi IIS, zdalne Lokacje i FTP.

- Projekty systemu plików są tworzone w ścieżce lokalnej, ale nie wymagają instalacji Internet Information Services (IIS), ponieważ są one dostępne wewnętrznie za pośrednictwem ścieżki UNC i mogą być umieszczone pod kontrolą źródła z wnętrza IDE, podobnie jak w przypadku projektów klientów.

- Lokalne projekty usług IIS współpracują z usługami IIS, które są zainstalowane na tym samym komputerze i są dostępne z adresem URL wskazującym na maszynę lokalną.

- Projekty witryn zdalnych są również tworzone w ramach usług IIS, ale znajdują się pod kontrolą źródła na komputerze serwera usług IIS, a nie w środowisku [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- Dostęp do projektów FTP odbywa się za pomocą zdalnego serwera FTP, ale nie można ich umieścić pod kontrolą źródła.

  Wyklucz inny termin dla rozwiązania lub projektu pod kontrolą źródła.

  Wersja magazynu wersji bazy danych kontroli źródła, która jest dostępna za pomocą interfejsu API wtyczki kontroli źródła.

## <a name="test-areas-covered-in-this-section"></a>Obszary testowe omówione w tej sekcji

- [Obszar testowy 1: dodawanie do kontroli kodu źródłowego i otwieranie z poziomu kontroli kodu źródłowego](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Przypadek 1a: Dodawanie rozwiązania do kontroli źródła

  - Przypadek 1b: Otwórz rozwiązanie z kontroli źródła

  - Przypadek 1c: Dodawanie rozwiązania z kontroli źródła

- [Obszar testowy 2: pobieranie z kontroli kodu źródłowego](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Obszar testowy 3: wyewidencjonowywanie i cofanie wyewidencjonowania](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Przypadek 3: wyewidencjonowywanie/cofanie wyewidencjonowania

  - Przypadek 3A: wyewidencjonowywanie

  - Przypadek 3B: odłączono wyewidencjonowanie

  - Przypadek 3C: modyfikowanie zapytania/zapisywanie zapytania (QEQS)

  - Przypadek 3W: wyewidencjonowywanie dyskretne

  - Przypadek 3e: Cofnij wyewidencjonowanie

- [Obszar testowy 4: ewidencjonowanie](../../extensibility/internals/test-area-4-check-in.md)

  - Przypadek 4a: zmodyfikowane elementy

  - Przypadek 4B: Dodawanie plików

  - Przypadek 4C: Dodawanie projektów

- [Obszar testowy 5: zmiana kontroli kodu źródłowego](../../extensibility/internals/test-area-5-change-source-control.md)

  - Przypadek 5a: powiązanie

  - Przypadek 5B: Usuwanie powiązania

  - Przypadek 5c: rebind

- [Obszar testowy 6: Usuwanie](../../extensibility/internals/test-area-6-delete.md)

- [Obszar testowy 7: Udostępnij](../../extensibility/internals/test-area-7-share.md)

- [Obszar testowy 8: przełączanie wtyczki](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Przypadek 8a: Automatyczna zmiana

  - Przypadek 8b: zmiana oparta na rozwiązaniu

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)
