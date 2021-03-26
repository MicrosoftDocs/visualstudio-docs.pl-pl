---
title: Wtyczki kontroli źródła | Microsoft Docs
description: W artykułach w tej sekcji opisano pełną specyfikację interfejsu, która umożliwia integrację systemów kontroli źródła z programem Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a6788d738d37ac62156958acb15c1bcd5d536515
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089956"
---
# <a name="source-control-plug-ins"></a>Wtyczki kontroli źródła
Sekcja Dokumentacja zestawu SDK wtyczki kontroli źródła zawiera kompletną specyfikację interfejsu, która umożliwia zintegrowane systemy kontroli źródła [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Określa składnię i semantykę różnych funkcji i typów danych, które Wtyczka kontroli źródła musi zaimplementować do interfejsu za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE).

## <a name="in-this-section"></a>W tej sekcji
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md) Wyświetla listę funkcji, które muszą zostać zaimplementowane przez wtyczkę kontroli źródła w celu zapewnienia zgodności z interfejsem API kontroli źródła.

- [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md) Opisuje funkcje używane przez wtyczkę kontroli źródła do przekazywania informacji z powrotem do środowiska IDE podczas wykonywania niektórych poleceń.

- [Moduły wyliczające](../extensibility/enumerators.md) Wyświetla listę typów danych modułu wyliczającego w interfejsie API dodatku plug-in kontroli źródła, który musi znać Wtyczka kontroli źródła.

- [Flagi możliwości](../extensibility/capability-flags.md) Opisuje `SCC_CAP_xxx` flagi wskazujące możliwości dostawcy.

- [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) Wyświetla listę flag, które są przydatne w kontekście konkretnych poleceń.

- [Kody błędów](../extensibility/error-codes.md) Wyświetla listę typowych wartości błędów zwracanych przez funkcje jako `SCCTRN` .

- [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Opisuje klucze służące do uzyskiwania dostępu do rejestru w celu znalezienia wtyczki kontroli źródła.

- [MSSCCPRJ. Plik SCC](../extensibility/mssccprj-scc-file.md) zawiera opis pliku po stronie klienta, który zawiera informacje nieprzezroczyste dla IDE, ale jest używany przez wtyczkę kontroli źródła do lokalizowania rozwiązania lub projektu w kontroli wersji.

- [Najlepsze rozwiązania dotyczące implementowania wtyczki kontroli źródła](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Zawiera kolekcję ważnych przypomnień technicznych, które należy zapamiętać podczas wdrażania interfejsu API wtyczki kontroli źródła.

- [Ograniczenia długości ciągu](../extensibility/restrictions-on-string-lengths.md) Opisuje ograniczenia w interfejsie API dodatku plug-in kontroli źródła dla długości ciągów używanych w różnych funkcjach.

- [Słownik](../extensibility/source-control-plug-in-glossary.md) Zawiera przydatne warunki i ich definicje umożliwiające odczytywanie dokumentacji zestawu SDK dodatku do kontroli źródła.

- [Instrukcje: wyłączanie ostrzeżeń dotyczących zgodności dla wtyczek kontroli źródła](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Opisuje sposób wyłączania ostrzeżeń.

## <a name="related-sections"></a>Sekcje pokrewne
- [Przykład wtyczki kontroli źródła](https://www.microsoft.com/download/details.aspx?id=55984) Zapewnia przykład funkcji wtyczki kontroli źródła.

- [Przewodnik testowy dla wtyczek kontroli źródła](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Opisuje procedury testowania związane z wtyczką kontroli źródła.

- [Tworzenie wtyczki kontroli źródła](../extensibility/internals/creating-a-source-control-plug-in.md) W tym artykule omówiono sposób tworzenia wtyczki kontroli źródła, która udostępnia funkcje kontroli źródła podczas korzystania z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika kontroli źródła.

- [Dokumentacja zestawu Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md) Przedstawia listę tematów referencyjnych.
