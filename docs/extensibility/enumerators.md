---
title: Moduły wyliczające | Microsoft Docs
description: Informacje na temat typów danych modułu wyliczającego w interfejsie API dodatku plug-in kontroli źródła, w tym kod polecenia, komunikat, kod stanu pliku i kod stanu katalogu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0bdc42901cbdad3b30bb6739ec93b8979b0d56ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075279"
---
# <a name="enumerators"></a>Modułów wyliczających
Ta sekcja zawiera listę typów danych modułu wyliczającego w interfejsie API Plug-in kontroli źródła, które musi znać Wtyczka kontroli źródła.

## <a name="in-this-section"></a>W tej sekcji
- [Kod polecenia](../extensibility/command-code-enumerator.md) Wylicza opcje funkcji [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) i [SccPopulateList](../extensibility/sccpopulatelist-function.md) .

- [Komunikat](../extensibility/message-enumerator.md) Wylicza flagi używane dla wywołania zwrotnego drukowania, [lpTextOutProc](../extensibility/lptextoutproc.md).

- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md) Zawiera nazwane wartości stałe, które określają stan pliku w ramach kontroli źródła.

- [Kod stanu katalogu](../extensibility/directory-status-code-enumerator.md) Zawiera nazwane wartości stałe, które określają stan katalogu pod kontrolą źródła.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie wtyczki kontroli źródła](../extensibility/internals/creating-a-source-control-plug-in.md) Definiuje zestaw SDK wtyczki kontroli źródła i opisuje uwzględnione zasoby.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Monituje użytkownika o opcje zaawansowane dla danego polecenia.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Bada listę plików do ich bieżącego stanu. Ponadto program używa `pfnPopulate` funkcji do powiadamiania wywołującego, gdy plik jest niezgodny z kryteriami dla `nCommand` .

- [LpTextOutProc](../extensibility/lptextoutproc.md) Opisuje funkcję wywołania zwrotnego, która jest używana przez [SccOpenProject](../extensibility/sccopenproject-function.md) do wyświetlania komunikatów z wtyczki kontroli źródła za pośrednictwem IDE.

- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md) Zawiera kompletną listę wszystkich elementów w interfejsie API dodatku plug-in kontroli źródła.
