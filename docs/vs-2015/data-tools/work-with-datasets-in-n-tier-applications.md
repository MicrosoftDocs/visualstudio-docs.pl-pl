---
title: Pracuj z zestawami danych w aplikacjach n-warstwowych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f7be307ec94b15871da20ace8055fc7121d5d92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657814"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Praca z zestawami danych w aplikacjach n-warstwowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-warstwowe aplikacje danych * są aplikacjami zorientowanymi na dane, które są rozdzielone na wiele warstw logicznych (lub *warstw*). Innymi słowy, wielowarstwowa aplikacja do obsługi danych to aplikacja, która jest rozdzielona na wiele projektów, z warstwą dostępu do danych, warstwą logiki biznesowej i warstwą prezentacji w oddzielnym projekcie. Aby uzyskać więcej informacji, zobacz [Omówienie wielowarstwowych aplikacji do obsługi danych](../data-tools/n-tier-data-applications-overview.md).

 Wpisane zestawy danych zostały ulepszone, aby klasy TableAdapters i DataSet mogły być generowane w projektach dyskretnych. Dzięki temu można szybko oddzielić warstwy aplikacji i generować wielowarstwowe aplikacje do obsługi danych.

 Obsługa n-warstwowa w typach danych typu umożliwia iteracyjne programowanie architektury aplikacji do projektu n-warstwowego. Powoduje również usunięcie wymagania, aby ręcznie rozdzielić kod na więcej niż jeden projekt. Rozpocznij projektowanie warstwy danych przy użyciu Projektant obiektów Dataset. Gdy wszystko jest gotowe do przełączenia architektury aplikacji do projektu n-warstwowego, ustaw właściwość **projektu** DataSet zestawu danych, aby wygenerować klasę zestawu danych w osobnym projekcie.

## <a name="in-this-section"></a>W tej sekcji
 [Oddziel zestawy danych i TableAdapters je w różnych projektach](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md) Opisuje sposób przenoszenia wygenerowanej klasy zestawu danych z projektu, który zawiera wygenerowane klasy TableAdapter i nowy projekt.

 [Dodawanie kodu do TableAdapters w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) Opisuje sposób generowania klasy częściowej, w której można dodać kod dla n-warstwowej TableAdapter.

 [Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md) Opisuje sposób generowania klasy częściowej, w której można dodać kod dla n-warstwowego zestawu danych.

 [Dodawanie walidacji do n-warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md) Opisuje, gdzie dodać kod, aby przeprowadzić walidację zmiany danych.

 [Przewodnik: Tworzenie wielowarstwowej aplikacji danych](../data-tools/walkthrough-creating-an-n-tier-data-application.md) Zawiera instrukcje krok po kroku dotyczące tworzenia określonego zestawu danych i rozdzielania kodu TableAdapter i zestawu danych na wiele projektów.

 [Przewodnik: Dodawanie walidacji do wielowarstwowej aplikacji danych](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265) Zawiera instrukcje krok po kroku dotyczące dodawania walidacji do aplikacji, która została utworzona w przewodniku dotyczącym wielowarstwowej aplikacji do obsługi danych.

## <a name="reference"></a>Dokumentacja
 <xref:System.Data.DataSet>

 <xref:System.Data.TypedTableBase%601>

## <a name="related-sections"></a>Sekcje pokrewne

- [N-warstwowe aplikacje do obsługi danych — omówienie](../data-tools/n-tier-data-applications-overview.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)