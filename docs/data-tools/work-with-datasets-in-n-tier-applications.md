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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c7532bed6a7d43c24d698870723d2265fc2b176f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585928"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Praca z zestawami danych w aplikacjach n-warstwowych

*Wielowarstwowe aplikacje danych* to aplikacje zorientowane na dane, które są rozdzielone na wiele warstw logicznych (lub *warstw*). Innymi słowy, wielowarstwowa aplikacja do obsługi danych to aplikacja, która jest rozdzielona na wiele projektów, z warstwą dostępu do danych, warstwą logiki biznesowej i warstwą prezentacji w oddzielnym projekcie. Aby uzyskać więcej informacji, zobacz [Omówienie wielowarstwowych aplikacji do obsługi danych](../data-tools/n-tier-data-applications-overview.md).

Wpisane zestawy danych zostały ulepszone, aby klasy TableAdapters i DataSet mogły być generowane w projektach dyskretnych. Dzięki temu można szybko oddzielić warstwy aplikacji i generować wielowarstwowe aplikacje do obsługi danych.

Obsługa n-warstwowa w typach danych typu umożliwia iteracyjne programowanie architektury aplikacji do projektu n-warstwowego. Powoduje również usunięcie wymagania, aby ręcznie rozdzielić kod na więcej niż jeden projekt. Rozpocznij projektowanie warstwy danych przy użyciu **Projektant obiektów DataSet**. Gdy wszystko jest gotowe do przełączenia architektury aplikacji do projektu n-warstwowego, ustaw właściwość **projektu** DataSet zestawu danych, aby wygenerować klasę zestawu danych w osobnym projekcie.

## <a name="reference"></a>Dokumentacja

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Zobacz też

- [N-warstwowe aplikacje dotyczące danych — omówienie](../data-tools/n-tier-data-applications-overview.md)
- [Przewodnik: Tworzenie wielowarstwowej aplikacji danych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Dodawanie walidacji do n-warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md)
- [Aplikacje N-warstwowe i zdalne z LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)
