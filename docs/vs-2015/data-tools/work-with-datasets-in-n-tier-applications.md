---
title: Praca z zestawami danych w aplikacjach n warstwowych | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 38239bd431f3e66e1a694361f3727c843fbf29d3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558466"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Praca z zestawami danych w aplikacjach n-warstwowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikacje warstwowe — * są aplikacji biznesowych przetwarzających dane, które są rozdzielone na wiele warstw logiczne (lub *warstwy*). Innymi słowy aplikacja n warstwowa danych jest aplikacja, która jest dzielony na wiele projektów z warstwy dostępu do danych, warstwy logiki biznesowej i warstwy prezentacji każdego we własnym projekcie. Aby uzyskać więcej informacji, zobacz [N-warstwowa danych aplikacji — omówienie](../data-tools/n-tier-data-applications-overview.md).  
  
 Tak, aby klas TableAdapters i zestawu danych mogą być generowane w dyskretne projekty zostały rozszerzone typizowanych zestawów danych. Zapewnia to możliwość szybkiego oddzielnymi warstwami aplikacji i generowania aplikacji n warstwowa danych.  
  
 Obsługa N-warstwowej w typizowanych zbiorach danych umożliwia iteracyjne projektowanie architektury aplikacji n warstwowa projektowi. Usuwa wymaganie, aby ręcznie odseparowania kodu do więcej niż jeden projekt. Rozpocząć projektowanie warstwy danych za pomocą Projektanta obiektów Dataset. Gdy wszystko będzie gotowe, umożliwiające architektura n warstwowa projektu, należy ustawić **projektu DataSet** właściwości zestawu danych, aby wygenerować klasę zestawu danych do oddzielnego projektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 W tym artykule opisano sposób przenoszenia wygenerowaną klasę zestawu danych z projektu, który zawiera wygenerowane klasy TableAdapter z do nowego projektu.  
  
 [Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 W tym artykule opisano sposób generowania klasy częściowej, w którym można dodać kod TableAdapter n warstwowej.  
  
 [Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 W tym artykule opisano sposób generowania klasy częściowej, w którym można dodać kodu dla zestawu danych n warstwowej.  
  
 [Dodawanie walidacji do n-warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 W tym artykule opisano gdzie dodać kod do wykonywania sprawdzania poprawności od zmieniających się danych.  
  
 [Przewodnik: Tworzenie n-warstwowej aplikacji do obsługi danych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Instrukcje krok po kroku dotyczące tworzenia typizowany zestaw danych i oddzielenie kodu TableAdapter i zestaw danych do wielu projektów.  
  
 [Przewodnik: Dodawanie walidacji do aplikacji warstwowych](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
 Instrukcje krok po kroku do dodawania sprawdzania poprawności do aplikacji, który został utworzony w Przewodnik po aplikacji n warstwowa danych.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## <a name="related-sections"></a>Sekcje pokrewne

- [N-warstwowe aplikacje do obsługi danych — omówienie](../data-tools/n-tier-data-applications-overview.md)   
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)   
- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
- [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)