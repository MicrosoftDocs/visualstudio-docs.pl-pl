---
title: Praca z zestawami danych w aplikacjach n-warstwowych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c6da3f51a249aaf52cf3f20b90f3add6ceeb7aa1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936554"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Praca z zestawami danych w aplikacjach n-warstwowych

*Aplikacje warstwowe —* są aplikacji biznesowych przetwarzających dane, które są rozdzielone na wiele warstw logiczne (lub *warstwy*). Innymi słowy aplikacja n warstwowa danych jest aplikacja, która jest dzielony na wiele projektów z warstwy dostępu do danych, warstwy logiki biznesowej i warstwy prezentacji każdego we własnym projekcie. Aby uzyskać więcej informacji, zobacz [N-warstwowa danych aplikacji — omówienie](../data-tools/n-tier-data-applications-overview.md).

Tak, aby klas TableAdapters i zestawu danych mogą być generowane w dyskretne projekty zostały rozszerzone typizowanych zestawów danych. Zapewnia to możliwość szybkiego oddzielnymi warstwami aplikacji i generowania aplikacji n warstwowa danych.

Obsługa N-warstwowej w typizowanych zbiorach danych umożliwia iteracyjne projektowanie architektury aplikacji n warstwowa projektowi. Usuwa wymaganie, aby ręcznie odseparowania kodu do więcej niż jeden projekt. Rozpocząć projektowanie warstwę danych przy użyciu **Projektanta obiektów Dataset**. Gdy wszystko będzie gotowe, umożliwiające architektura n warstwowa projektu, należy ustawić **projektu DataSet** właściwości zestawu danych, aby wygenerować klasę zestawu danych do oddzielnego projektu.

## <a name="reference"></a>Tematy pomocy

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Zobacz także

- [Omówienie aplikacji N-warstwowa danych](../data-tools/n-tier-data-applications-overview.md)
- [Przewodnik: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Dodawanie walidacji do n-warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md)
- [N-warstwowe i zdalne aplikacje za pomocą LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)