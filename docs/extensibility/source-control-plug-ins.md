---
title: Wtyczki kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01e7a0ca8a509d430a0794a2cedb4b2e9d869585
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331828"
---
# <a name="source-control-plug-ins"></a>Wtyczki kontroli źródła
Sekcja dokumentacji zestawu SDK wtyczki kontroli źródła, zawiera specyfikację pełny interfejs, umożliwiająca systemów kontroli źródła można zintegrować z usługą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Określa, składnia i semantyka różne typy danych i funkcje, które wtyczka do kontroli źródła musi implementować interfejsu z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE).

## <a name="in-this-section"></a>W tej sekcji
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md) Wyświetla listę funkcji, które muszą zostać zaimplementowane przez wtyczka do kontroli źródła aby można było zgodne z interfejsem API wtyczki kontroli źródła.

- [Wywołanie zwrotne funkcje implementowane przez środowisko IDE](../extensibility/callback-functions-implemented-by-the-ide.md) Opisuje funkcje, których wtyczka do kontroli źródła używa do przekazania informacji do środowiska IDE, podczas gdy niektóre polecenia zostaną wykonane.

- [Moduły wyliczające](../extensibility/enumerators.md) zawiera listę typów danych modułu wyliczającego w interfejsie API wtyczki kontroli źródła wtyczka do kontroli źródła należy wiedzieć o.

- [Flagi możliwości](../extensibility/capability-flags.md) w tym artykule opisano `SCC_CAP_xxx` flagi wskazujące możliwości dostawcy.

- [Flagi bitowe używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) Wyświetla listę flag, które są przydatne w kontekście określonego polecenia.

- [Kody błędów](../extensibility/error-codes.md) wymieniono typowe wartości błędów zwracanych przez funkcje jako `SCCTRN`.

- [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) opisano klucze na potrzeby uzyskiwania dostępu do rejestru, aby znaleźć wtyczka do kontroli źródła.

- [MSSCCPRJ. Plik SCC](../extensibility/mssccprj-scc-file.md) opis zawierający informacje nieprzezroczysta dla środowiska IDE, ale używanego przez wtyczka do kontroli źródła, aby znaleźć rozwiązania lub projektu w kontroli wersji pliku po stronie klienta.

- [Najlepsze rozwiązania dotyczące wdrażania wtyczki kontroli źródła](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) zawiera zbiór ważne przypomnienia Technical Preview do zapamiętania, natomiast w przypadku implementowania interfejsu API wtyczki kontroli źródła.

- [Ograniczenia długości ciągów](../extensibility/restrictions-on-string-lengths.md) opisano ograniczenia w interfejsie API wtyczki kontroli źródła na długości ciągów używanych w różnych funkcji.

- [Słownik](../extensibility/source-control-plug-in-glossary.md) udostępnia przydatne warunki i ich definicje dla odczytu w dokumentacji zestawu SDK wtyczki kontroli źródła.

- [Instrukcje: Włącz wyłączanie ostrzeżenia dotyczącego zgodności dla wtyczek kontroli źródła](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) zawiera opis sposobu wyłączania ostrzeżeń.

## <a name="related-sections"></a>Sekcje pokrewne
- [Przykładowe wtyczki kontroli źródła](https://www.microsoft.com/download/details.aspx?id=55984) zawiera przykładowy funkcji wtyczki kontroli źródła.

- [Przewodnik wtyczki kontroli źródła testowania](../extensibility/internals/test-guide-for-source-control-plug-ins.md) opisano procedury badania dotyczące wtyczki kontroli źródła.

- [Tworzenie wtyczki kontroli źródła](../extensibility/internals/creating-a-source-control-plug-in.md) w tym artykule omówiono sposób tworzenia wtyczki kontroli źródła dostarczającego funkcji kontroli źródła, gdy używasz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika kontroli źródła (UI).

- [Odwołanie do zestawu SDK programu Visual Studio](../extensibility/visual-studio-sdk-reference.md) Wyświetla listę tematów odwołań.