---
title: Aplikacje warstwowe — Przegląd
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 00bd9dff41e6c57fc6969f4198f96d0e209e2a77
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55943692"
---
# <a name="n-tier-data-applications-overview"></a>Omówienie aplikacji N-warstwowa danych
*N-warstwowa* dane aplikacji są aplikacje danych, które są rozdzielone na wiele *warstwy*. Ich inne nazwy to „aplikacje rozproszone” i „aplikacje wielowarstwowe”. Aplikacje n-warstwowe dzielą przetwarzanie na dyskretne warstwy, które są rozkładane między klienta i serwer. Podczas tworzenia aplikacji uzyskujących dostęp do danych należy jednoznacznie odseparować różne warstwy tworzące aplikację.

Typowa aplikacja n-warstwowa zawiera warstwę prezentacji, warstwę środkową i warstwę danych. Najłatwiejszym sposobem rozdzielenia różnych warstw w n-warstwowej aplikacji jest utworzenie dyskretnych projektów dla każdej warstwy, która ma się znaleźć w aplikacji. Na przykład warstwą prezentacji może być aplikacja środowiska Windows Forms, podczas gdy logiką dostępu do danych może być biblioteka klas umieszczona w warstwie środkowej. Ponadto warstwa prezentacji może się komunikować z logiką dostępu do danych w warstwie środkowej za pośrednictwem usługi. Rozdzielanie składników aplikacji w oddzielne warstwy ułatwia konserwację i zwiększa skalowalność aplikacji. Wynika to z możliwości łatwiejszego wprowadzania nowych technologii do poszczególnych warstw, bez konieczności zmiany projektu całego rozwiązania. Dodatkowo zazwyczaj n-warstwowe aplikacje przechowują wrażliwe informacje w środkowej warstwie, która utrzymuje izolację od warstwy prezentacji.

Program Visual Studio zawiera kilka funkcji, które ułatwiają deweloperom tworzenie aplikacji n-warstwowych:

-   Zestaw danych dostarcza **projektu DataSet** właściwość, która umożliwia rozdzielenie zestawu danych (warstwy jednostek danych) i TableAdapter (Warstwa dostępu do danych) w dyskretne projekty.

-   [LINQ to SQL tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) zawiera ustawienia umożliwiające Generowanie klasy DataContext i danych do oddzielnych przestrzeni nazw. Takie rozwiązania pozwala logicznie rozdzielić warstwy dostępu do danych i jednostek danych.

-   [LINQ do SQL](/dotnet/framework/data/adonet/sql/linq/index) zapewnia <xref:System.Data.Linq.Table%601.Attach%2A> metodę, która umożliwia łączenie kontekstu danych z różnych warstw w aplikacji. Aby uzyskać więcej informacji, zobacz [N-warstwowe i zdalne aplikacje za pomocą LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql).

## <a name="presentation-tier"></a>Warstwa prezentacji
*Warstwa prezentacji* jest warstwą, gdzie użytkownicy dokonują interakcji z aplikacją. Często zawiera także dodatkową logikę aplikacji. Oto typowe składniki warstwy prezentacji:

-   Składniki powiązania danych, takie jak <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator>.

-   Obiektowe reprezentacje danych, takie jak [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) klas jednostek do użycia w warstwie prezentacji.

Warstwa prezentacji zwykle uzyskuje dostęp do warstwy środkowej za pomocą odwołania do usługi (na przykład [Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) aplikacji). Warstwa prezentacji nie uzyskuje bezpośredniego dostępu do warstwy danych. Warstwa prezentacji komunikuje się z warstwą danych za pomocą składnika dostępu do danych w warstwie środkowej.

## <a name="middle-tier"></a>Warstwa środkowa
*Warstwy środkowej* jest warstwy, która warstwa prezentacji i danych jest używany do komunikowania się ze sobą. Oto typowe składniki warstwy środkowej:

-   Logika biznesowa, taka jak reguły biznesowe i mechanizmy sprawdzania poprawności danych.

-   Składniki i logika dostępu do danych, w tym:

    -   [TableAdapters](create-and-configure-tableadapters.md) i [DataAdapter i DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

    -   Obiektowe reprezentacje danych, takie jak [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) klas jednostek.

    -   Wspólne usługi aplikacji, takie jak uwierzytelnianie, autoryzacja i personalizacja.

Na ilustracji poniżej widać funkcje i technologie, które są dostępne w programie Visual Studio i mogą być umieszczone w środkowej warstwie aplikacji n-warstwowej.

![Na środku składniki warstwy](../data-tools/media/ntiermid.png) warstwy środkowej

Warstwa środkowa zazwyczaj łączy się z warstwą danych przy użyciu połączenia danych. To połączenie danych jest zazwyczaj przechowywane w składniku dostępu do danych.

## <a name="data-tier"></a>Warstwa danych
*Warstwy danych* to w zasadzie serwer przechowujący dane aplikacji (na przykład serwer działa program SQL Server).

Na ilustracji poniżej widać funkcje i technologie, które są dostępne w programie Visual Studio i mogą być umieszczone w warstwie danych aplikacji n-warstwowej.

![Warstwa danych składników](../data-tools/media/ntierdatatier.png) warstwy danych

Warstwa danych nie może być dostępna bezpośrednio z klienta w warstwie prezentacji. Zamiast tego składnik dostępu do danych w warstwie środkowej obsługuje komunikację między warstwami prezentacji i danych.

## <a name="help-for-n-tier-development"></a>Pomoc dotycząca programowania n warstwowej
Poniższe tematy zawierają informacje dotyczące pracy z aplikacjami n-warstwowymi:

[Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[Przewodnik: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[N-warstwowe i zdalne aplikacje za pomocą LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)