---
title: Wyliczacze | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee48d064612e5519d5ad7e5eaf04de6c5a697837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711853"
---
# <a name="enumerators"></a>Modułów wyliczających
W tej sekcji wymieniono typy danych modułu wyliczacza w interfejsie API dodatku Dodatku Kontroli źródła, o których musi wiedzieć wtyczka kontroli źródła.

## <a name="in-this-section"></a>W tej sekcji
- [Kod polecenia](../extensibility/command-code-enumerator.md) Wylicza opcje [dla funkcji SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) i [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

- [Wiadomość](../extensibility/message-enumerator.md) Wylicza flagi używane do wywołania zwrotnego drukowania, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md) Zawiera nazwane wartości stałe, które określają stan pliku pod kontrolą źródła.

- [Kod stanu katalogu](../extensibility/directory-status-code-enumerator.md) Zawiera nazwane wartości stałe, które określają stan katalogu pod kontrolą źródła.

## <a name="related-sections"></a>Powiązane sekcje
- [Tworzenie wtyczki formantu źródła](../extensibility/internals/creating-a-source-control-plug-in.md) Definiuje sdk wtyczki kontroli źródła i opisuje dołączone zasoby.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Monituje użytkownika o zaawansowane opcje dla danego polecenia.

- [Lista SccPopulateList](../extensibility/sccpopulatelist-function.md) Sprawdza listę plików pod kątem ich bieżącego stanu. Ponadto używa `pfnPopulate` tej funkcji do powiadamiania rozmówcy, gdy plik nie `nCommand`spełnia kryteriów programu .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) W tym artykule opisano funkcję wywołania zwrotnego, która jest używana przez [SccOpenProject](../extensibility/sccopenproject-function.md) do wyświetlania komunikatów z wtyczki formantu źródłowego za pośrednictwem IDE.

- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md) Zawiera pełną listę wszystkich elementów w interfejsie API wtyczki kontroli źródła.
