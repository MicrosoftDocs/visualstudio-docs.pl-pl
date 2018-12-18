---
title: Wyświetlanie powiązanych danych w aplikacjach WPF
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f37fdeb7ddd305c7c258958d92c08cf1d8f2a4a8
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304600"
---
# <a name="display-related-data-in-wpf-applications"></a>Wyświetlanie powiązanych danych w aplikacjach WPF

W niektórych aplikacjach można pracować z danymi, które pochodzą z wielu tabel lub jednostek, które są powiązane ze sobą w relacji nadrzędny podrzędny. Na przykład możesz chcieć wyświetlić siatkę, na którym są wyświetlani klienci z `Customers` tabeli. Gdy użytkownik wybierze określonego odbiorcy, inny Siatka wyświetla zamówień tego klienta z powiązanych `Orders` tabeli.

Możesz utworzyć formanty powiązane z danymi, które wyświetlają pokrewne dane przez przeciąganie elementów z **źródeł danych** okna Projektanta WPF.

## <a name="to-create-controls-that-display-related-records"></a>Aby utworzyć formanty, które wyświetlania powiązanych rekordów

1. Na **danych** menu, kliknij przycisk **Pokaż źródła danych** otworzyć **źródeł danych** okna.

2. Kliknij przycisk **Dodaj nowe źródło danych**i wykonaj **konfiguracji źródła danych** kreatora.

3. Otwórz projektanta WPF i upewnij się, że projektant zawiera kontener, który jest prawidłowe miejsca docelowego dla elementów w **źródeł danych** okna.

     Aby uzyskać więcej informacji na temat prawidłowych miejsc upuszczania zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

4. W **źródeł danych** okna, rozwiń węzeł, który reprezentuje tabeli nadrzędnej lub obiekt w relacji. Tabela nadrzędna lub obiekt znajduje się na stronie "jeden" w relacji jeden do wielu.

5. Przeciągnij z węzła nadrzędnego (lub wszystkie poszczególne elementy w węźle nadrzędnym) **źródeł danych** okna na prawidłowe miejsca docelowego w projektancie.

     Program Visual Studio generuje XAML, który tworzy nowe formanty powiązane z danymi dla każdego elementu, który możesz przeciągnąć. XAML również dodaje nowy <xref:System.Windows.Data.CollectionViewSource> tabeli nadrzędnej lub obiektu do zasobów miejsca docelowego. Dla niektórych źródeł danych programu Visual Studio generuje kod, aby załadować dane do tabeli nadrzędnej lub obiektu. Aby uzyskać więcej informacji, zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. W **źródeł danych** oknie Znajdź pokrewną tabelę podrzędną lub obiektu. Podrzędnych względem tabel i obiektów są traktowane jako węzły można rozwijać w dolnej części listy danych węzła nadrzędnego.

7. Przeciągnij węzeł podrzędny (lub wszystkie poszczególne elementy węzła podrzędnego) z **źródeł danych** okna na prawidłowe miejsca docelowego w projektancie.

     Program Visual Studio generuje XAML, który tworzy nowe formanty powiązane z danymi dla każdego z elementów, które przeciągniesz. XAML również dodaje nowy <xref:System.Windows.Data.CollectionViewSource> tabeli podrzędnej lub obiektu do zasobów miejsca docelowego. Ta nowa <xref:System.Windows.Data.CollectionViewSource> jest powiązana z właściwością tabeli nadrzędnej lub obiekt, który właśnie został przeciągnięty do projektanta. Dla niektórych źródeł danych programu Visual Studio generuje kod, aby załadować dane do tabeli podrzędnej lub obiektu.

     Na poniższym rysunku pokazano powiązane **zamówienia** tabeli **klientów** tabeli w zestawie danych w **źródeł danych** okna.

     ![Relacje przedstawiający okno źródła danych](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Tworzenie tabel wyszukiwania w aplikacjach WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)