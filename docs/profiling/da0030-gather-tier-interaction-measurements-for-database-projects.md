---
title: DA0030 — Zbieraj pomiary interakcji warstw dla projektów bazy danych | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e5cff8f76743119409366a0e52d71070d62a9b82
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332360"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Zbieraj pomiary interakcji między warstwami dla projektów bazy danych

|||
|-|-|
|Identyfikator reguły|DA0030|
|Kategoria|Użycie narzędzia profilowania|
|Metoda profilowania|Próbkowanie|
|Komunikat|Zebranie pomiarów interakcji dla aplikacji wielowarstwowych pomoże Ci zrozumieć wzorce użycia bazy danych oraz opóźnienia dostępu do danych. Spróbuj ponownie profilować aplikację, korzystając z włączonej opcji profilowania interakcji między warstwami.|
|Typ reguły|Informacje|

## <a name="cause"></a>Przyczyna
 Wywołania <xref:System.Data> metod są znaczną częścią danych profilowania, a dane interakcji warstwy nie są zbierane w ramach uruchomienia profilowania. Rozważ ponowne przeprowadzenie profilowania i dodanie danych interakcji między warstwami.

## <a name="rule-description"></a>Opis reguły
 Ta zasada jest uruchamiana zawsze, gdy w funkcjach, które znajdują się w przestrzeni nazw System. Data, w tym <xref:System.Data.Linq> <xref:System.Data.Linq> .

 Aplikacje wielowarstwowe wykorzystują usługi warstwowe do prezentacji i warstw danych. Często warstwa danych jest osobnym procesem z uruchomionym systemem zarządzania bazami danych, takim jak Microsoft SQL Server. Warstwa danych może nawet być uruchomiona na oddzielnym komputerze od reszty aplikacji. Profile próbkowania zapewniają niewielki wgląd w funkcje i usługi działające poza procesem lub zdalnie.

 Narzędzia profilowania mogą zbierać informacje o chronometrażu dla aplikacji wielowarstwowych, które współpracują z warstwą danych Microsoft SQL Server przy użyciu wywołań asynchronicznych usługi ADO.NET Services. Należy jawnie włączyć profilowanie interakcji między warstwami. Nie jest on domyślnie włączony.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ta reguła służy tylko do celów informacyjnych i może nie wymagać czynności naprawczych.

 Aby uzyskać informacje na temat dodawania danych interakcji warstwy do profilowania danych z programu Visual Studio IDE, zobacz [zbieranie danych o interakcji warstwy](../profiling/collecting-tier-interaction-data.md). Aby uzyskać informacje na temat dodawania danych interakcji warstwy z wiersza polecenia, zobacz [zbieranie danych o interakcji z warstwą](../profiling/adding-tier-interaction-data-from-the-command-line.md).
