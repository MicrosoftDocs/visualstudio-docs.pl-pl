---
title: Moduły wyliczające | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37f469ecc0ae097592a128b30a6a6f189d58d94b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689749"
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