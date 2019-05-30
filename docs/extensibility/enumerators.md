---
title: Moduły wyliczające | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d3a0876dfd3a9d7b9cc86b18f6e9a6ba3b780d3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334508"
---
# <a name="enumerators"></a>Modułów wyliczających
W tej sekcji przedstawiono typy danych modułu wyliczającego w interfejsie API wtyczki kontroli źródła wtyczka do kontroli źródła należy wiedzieć o.

## <a name="in-this-section"></a>W tej sekcji
- [Polecenie kodu](../extensibility/command-code-enumerator.md) Wylicza opcje [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) i [SccPopulateList](../extensibility/sccpopulatelist-function.md) funkcji.

- [Komunikat](../extensibility/message-enumerator.md) Wylicza flagi używane do drukowania wywołanie zwrotne, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md) zawiera nazwanych stałych, określające stan pliku objętego kontrolą źródła.

- [Kod stanu katalogu](../extensibility/directory-status-code-enumerator.md) zawiera nazwanych stałych, określające stan katalogu pod kontrolą źródła.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie wtyczki kontroli źródła](../extensibility/internals/creating-a-source-control-plug-in.md) definiuje zestaw SDK wtyczki kontroli źródła i opisuje dołączone zasoby.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) monituje o określenie opcji zaawansowanych dla danego polecenia.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) sprawdza, czy lista plików dla ich bieżący stan. Ponadto używa `pfnPopulate` funkcję, aby powiadomić obiekt wywołujący, gdy plik jest niezgodny z kryteriami, które dla `nCommand`.

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) zawiera opis funkcji wywołania zwrotnego, który jest używany przez [SccOpenProject](../extensibility/sccopenproject-function.md) umożliwiające wyświetlanie komunikatów z kontroli źródła wtyczek za pośrednictwem środowiska IDE.

- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md) zawiera pełną listę wszystkich elementów w interfejsie API wtyczki kontroli źródła.