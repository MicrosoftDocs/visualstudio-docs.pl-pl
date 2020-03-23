---
title: 'DA0030: Zbieranie pomiarów interakcji warstwowych dla projektów bazy danych | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 26b0905882ef8ec2e3fcddc4cf699ecae7dbe7a4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777479"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Zbieranie pomiarów interakcji warstwy dla projektów bazy danych

|||
|-|-|
|Identyfikator reguły|DA0030|
|Kategoria|Użycie narzędzi profilowania|
|Metoda profilowania|Próbkowanie|
|Komunikat|Zbieranie pomiarów interakcji dla aplikacji wielowarstwowych pomoże Ci zrozumieć wzorce użycia bazy danych i opóźnienia w dostępie do kluczowych danych. Spróbuj ponownie profilować aplikację z włączoną opcją profilowania interakcji warstwy.|
|Typ reguły|Informacje|

## <a name="cause"></a>Przyczyna
 Wywołania <xref:System.Data> metod są znaczną część danych profilowania i nie zostały zebrane dane interakcji warstwy w przebiegu profilowania. Rozważ profilowanie ponownie i dodanie danych interakcji warstwy.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana za każdym razem, gdy istnieje znacząca <xref:System.Data.Linq> <xref:System.Data.Linq>aktywność w funkcjach, które znajdują się w przestrzeniach nazw System.Data, w tym .

 Aplikacje wielowarstwowe używają usług warstwowych do prezentacji i warstw danych. Często warstwa danych jest oddzielnym procesem z systemem zarządzania bazą danych, takim jak Microsoft SQL Server. Warstwa danych może nawet działać na oddzielnym komputerze od reszty aplikacji. Profile próbkowania zapewniają niewielki wgląd w funkcje i usługi działające poza procesem lub zdalnie.

 Narzędzia profilowania mogą zbierać informacje o chronometrażu dla aplikacji wielowarstwowych, które wchodzą w interakcję z warstwą danych programu Microsoft SQL Server przy użyciu asynchroniicznych wywołań ADO.NET usług. Należy jawnie włączyć profilowanie interakcji warstwy. Nie jest domyślnie włączona.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ta reguła służy wyłącznie do celów informacyjnych i może nie wymagać działań naprawczych.

 Aby uzyskać informacje dotyczące dodawania danych interakcji warstwy do danych profilowania z ide programu Visual Studio, zobacz [Zbieranie danych interakcji warstwy](../profiling/collecting-tier-interaction-data.md). Aby uzyskać informacje dotyczące dodawania danych interakcji warstwy z wiersza polecenia, zobacz [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md).
