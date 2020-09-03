---
title: N-warstwowe aplikacje dotyczące danych — omówienie | Microsoft Docs
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
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c8e0b0eb1c1016ac8e5351ff55df23b44d26824
ms.sourcegitcommit: a3edc753c951f317b67ce294cd2fc74f0c45390c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2020
ms.locfileid: "89426710"
---
# <a name="n-tier-data-applications-overview"></a>Aplikacje warstwowe — Przegląd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*N-warstwowe* aplikacje danych to aplikacje danych, które są rozdzielone na wiele *warstw*. Ich inne nazwy to „aplikacje rozproszone” i „aplikacje wielowarstwowe”. Aplikacje n-warstwowe dzielą przetwarzanie na dyskretne warstwy, które są rozkładane między klienta i serwer. Podczas tworzenia aplikacji uzyskujących dostęp do danych należy jednoznacznie odseparować różne warstwy tworzące aplikację.

 Typowa aplikacja n-warstwowa zawiera warstwę prezentacji, warstwę środkową i warstwę danych. Najłatwiejszym sposobem rozdzielenia różnych warstw w n-warstwowej aplikacji jest utworzenie dyskretnych projektów dla każdej warstwy, która ma się znaleźć w aplikacji. Na przykład warstwą prezentacji może być aplikacja środowiska Windows Forms, podczas gdy logiką dostępu do danych może być biblioteka klas umieszczona w warstwie środkowej. Ponadto warstwa prezentacji może się komunikować z logiką dostępu do danych w warstwie środkowej za pośrednictwem usługi. Rozdzielanie składników aplikacji w oddzielne warstwy ułatwia konserwację i zwiększa skalowalność aplikacji. Wynika to z możliwości łatwiejszego wprowadzania nowych technologii do poszczególnych warstw, bez konieczności zmiany projektu całego rozwiązania. Dodatkowo zazwyczaj n-warstwowe aplikacje przechowują wrażliwe informacje w środkowej warstwie, która utrzymuje izolację od warstwy prezentacji.

 Program Visual Studio zawiera kilka funkcji, które ułatwiają deweloperom tworzenie aplikacji n-warstwowych:

- Projektant zestawu danych udostępnia właściwość **projektu zestawu** danych, która umożliwia rozdzielenie zestawu danych (warstwy jednostek danych) i `TableAdapter` s (warstwa dostępu do danych) na projekty dyskretne.

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) udostępniają ustawienia umożliwiające wygenerowanie elementów DataContext i Data w oddzielnych obszarach nazw. Takie rozwiązania pozwala logicznie rozdzielić warstwy dostępu do danych i jednostek danych.

- [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) udostępnia <xref:System.Data.Linq.Table%601.Attach%2A> metodę, która umożliwia łączenie DataContext z różnych warstw w aplikacji. Aby uzyskać więcej informacji, zobacz [aplikacje N-warstwowe i zdalne za pomocą LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598).

## <a name="presentation-tier"></a>Warstwa prezentacji
 *Warstwa prezentacji* to warstwa, w której użytkownicy współpracują z aplikacją. Często zawiera także dodatkową logikę aplikacji. Oto typowe składniki warstwy prezentacji:

- Składniki powiązania danych, takie jak <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator>.

- Obiektowe reprezentacje danych, takie jak klasy jednostek [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) do użycia w warstwie prezentacji.

  Warstwa prezentacji zwykle uzyskuje dostęp do warstwy środkowej przy użyciu odwołania do usługi (na przykład [Windows Communication Foundation usług i usługi danych programu WCF w aplikacji Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) ). Warstwa prezentacji nie uzyskuje bezpośredniego dostępu do warstwy danych. Warstwa prezentacji komunikuje się z warstwą danych za pomocą składnika dostępu do danych w warstwie środkowej.

## <a name="middle-tier"></a>Warstwa środkowa
 *Warstwa środkowa* jest warstwą, której warstwa prezentacji i warstwa danych używają do komunikacji ze sobą. Oto typowe składniki warstwy środkowej:

- Logika biznesowa, taka jak reguły biznesowe i mechanizmy sprawdzania poprawności danych.

- Składniki i logika dostępu do danych, w tym:

  - [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) oraz [dataadaptery i DataReader](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

  - Obiektowe reprezentacje danych, takie jak klasy jednostek [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) .

  - Wspólne usługi aplikacji, takie jak uwierzytelnianie, autoryzacja i personalizacja.

  Na ilustracji poniżej widać funkcje i technologie, które są dostępne w programie Visual Studio i mogą być umieszczone w środkowej warstwie aplikacji n-warstwowej.

  ![Składniki warstwy środkowej](../data-tools/media/ntiermid.png "NtierMid") Warstwa środkowa

  Warstwa środkowa zazwyczaj łączy się z warstwą danych przy użyciu połączenia danych. To połączenie danych jest zazwyczaj przechowywane w składniku dostępu do danych.

## <a name="data-tier"></a>Warstwa danych
 *Warstwa danych* jest zasadniczo serwerem, w którym są przechowywane dane aplikacji (na przykład serwer z systemem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ).

 Na ilustracji poniżej widać funkcje i technologie, które są dostępne w programie Visual Studio i mogą być umieszczone w warstwie danych aplikacji n-warstwowej.

 ![Składniki warstwy danych](../data-tools/media/ntierdatatier.png "ntierdatatier") Warstwa danych

 Warstwa danych nie może być dostępna bezpośrednio z klienta w warstwie prezentacji. Zamiast tego składnik dostępu do danych w warstwie środkowej obsługuje komunikację między warstwami prezentacji i danych.

## <a name="help-for-n-tier-development"></a>Pomoc dotycząca tworzenia aplikacji n-warstwowych
 Poniższe tematy zawierają informacje dotyczące pracy z aplikacjami n-warstwowymi:

 [Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

 [Przewodnik: tworzenie n-warstwowych aplikacji do obsługi danych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

 [Przewodnik: Dodawanie walidacji do wielowarstwowej aplikacji danych](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)

 [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

## <a name="see-also"></a>Zobacz też
 <xref:System.Data.Linq.ITable.Attach%2A>Wskazówki [: Tworzenie wielowarstwowych aplikacji do obsługi danych,](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [hierarchicznych narzędzi aktualizacji](../data-tools/hierarchical-update.md) [w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) [dostęp do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
