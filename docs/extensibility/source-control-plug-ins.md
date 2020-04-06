---
title: Wtyczki kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc5f092e0ae93109d071af0b1a67999947e73e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699889"
---
# <a name="source-control-plug-ins"></a>Wtyczki kontroli źródła
Sekcja referencyjna SDK wtyczki source control zawiera pełną specyfikację interfejsu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]która umożliwia zintegrowanie systemów sterowania źródłami z programem . Określa składnię i semantytykę różnych funkcji i typów danych, które wtyczka kontroli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] źródła musi zaimplementować do interfejsu ze zintegrowanym środowiskiem programistycznym (IDE).

## <a name="in-this-section"></a>W tej sekcji
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md) Wyświetla listę funkcji, które muszą być zaimplementowane przez wtyczkę kontroli źródła w celu zapewnienia zgodności z interfejsem API wtyczki kontroli źródła.

- [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md) W tym artykule opisano funkcje, które wtyczka kontroli źródła używa do przekazywania informacji z powrotem do IDE, podczas gdy niektóre polecenia są wykonywane.

- [Wyliczacze](../extensibility/enumerators.md) Wyświetla listę typów danych modułu wyliczacza w interfejsie API dodatku Plug-in forżowania źródła, o których musi wiedzieć wtyczka kontroli źródła.

- [Flagi możliwości](../extensibility/capability-flags.md) W `SCC_CAP_xxx` tym artykule opisano flagi, które wskazują możliwości dostawcy.

- [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) Wyświetla listę flag, które są przydatne w kontekście poszczególnych poleceń.

- [Kody błędów](../extensibility/error-codes.md) Wyświetla listę typowych wartości `SCCTRN`błędów zwracanych przez funkcje jako .

- [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) W tym artykule opisano klucze dostępu do rejestru w celu znalezienia wtyczki kontroli źródła.

- [MSSCCPRJ. Plik SCC](../extensibility/mssccprj-scc-file.md) opisuje plik po stronie klienta, który zawiera informacje nieprzezroczyste dla IDE, ale który jest używany przez wtyczkę kontroli źródła, aby zlokalizować rozwiązanie lub projekt w kontroli wersji.

- [Najważniejsze wskazówki dotyczące implementowania wtyczki kontroli źródła](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Zawiera zbiór ważnych przypomnień technicznych do zapamiętania podczas implementowania interfejsu API wtyczki kontroli źródła.

- [Ograniczenia dotyczące długości ciągów](../extensibility/restrictions-on-string-lengths.md) W tym artykule opisano ograniczenia w interfejsie API wtyczki kontroli źródła na długości ciągów używanych w różnych funkcjach.

- [Słowniczek](../extensibility/source-control-plug-in-glossary.md) Zawiera przydatne terminy i ich definicje do czytania dokumentacji SDK wtyczki source control.

- [Jak: Wyłącz ostrzeżenia o zgodności dla wtyczek kontroli źródła](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) W tym artykule opisano sposób wyłączania ostrzeżeń.

## <a name="related-sections"></a>Sekcje pokrewne
- [Przykład wtyczki kontroli źródła](https://www.microsoft.com/download/details.aspx?id=55984) Udostępnia przykładową funkcję wtyczki kontroli źródła.

- [Przewodnik po testach dla wtyczek kontroli źródła](../extensibility/internals/test-guide-for-source-control-plug-ins.md) W tym artykule opisano procedury testowania związane z wtyczką kontroli źródła.

- [Tworzenie wtyczki kontroli źródła](../extensibility/internals/creating-a-source-control-plug-in.md) W tym artykule omówiono sposób tworzenia wtyczki kontroli źródła, która [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dostarcza funkcje kontroli źródła podczas korzystania z interfejsu użytkownika kontroli źródła (UI).

- [Odwołanie do sdk programu Visual Studio](../extensibility/visual-studio-sdk-reference.md) Przedstawia listę tematów referencyjnych.
