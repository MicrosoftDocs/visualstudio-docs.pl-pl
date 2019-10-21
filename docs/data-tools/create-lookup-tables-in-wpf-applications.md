---
title: Tworzenie tabel wyszukiwania w aplikacjach WPF
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a2a2179a759bc11a9466361d3c8cc2df45c12f20
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648596"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Tworzenie tabel wyszukiwania w aplikacjach WPF

Termin *tabela wyszukiwania* (nazywana czasem *powiązaniem wyszukiwania*) opisuje kontrolkę wyświetlającą informacje z jednej tabeli danych na podstawie wartości pola klucza obcego w innej tabeli. Tabelę odnośników można utworzyć, przeciągając główny węzeł tabeli nadrzędnej lub obiektu w oknie **źródła danych** na kontrolkę, która jest już powiązana z kolumną lub właściwością w powiązanej tabeli podrzędnej.

Na przykład rozważmy tabelę `Orders` w bazie danych sprzedaży. Każdy rekord w tabeli `Orders` zawiera `CustomerID`, który wskazuje, który klient złożył zamówienie. @No__t_0 jest kluczem obcym wskazującym rekord klienta w tabeli `Customers`. Po wyświetleniu listy zamówień z tabeli `Orders` może być konieczne wyświetlenie rzeczywistej nazwy klienta zamiast `CustomerID`. Ponieważ nazwa klienta znajduje się w tabeli `Customers`, należy utworzyć tabelę odnośników, aby wyświetlić nazwę klienta. Tabela wyszukiwania używa wartości `CustomerID` w rekordzie `Orders` do nawigowania po relacji i zwraca nazwę klienta.

## <a name="to-create-a-lookup-table"></a>Aby utworzyć tabelę odnośników

1. Dodaj jeden z następujących typów źródeł danych z danymi powiązanymi do projektu:

    - Zestaw danych lub Entity Data Model.

    - Usługa danych programu WCF, usługa WCF lub usługa sieci Web. Aby uzyskać więcej informacji, zobacz [jak: łączenie z danymi w usłudze](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Elementy. Aby uzyskać więcej informacji, zobacz [powiąż z obiektami w programie Visual Studio](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Aby można było utworzyć tabelę odnośników, muszą istnieć dwie powiązane tabele lub obiekty jako źródło danych dla projektu.

2. Otwórz **projektanta WPF**i upewnij się, że projektant zawiera kontener, który jest prawidłowym obiektem docelowym upuszczania dla elementów w oknie **źródła danych** .

     Aby uzyskać więcej informacji na temat prawidłowych obiektów docelowych upuszczania, zobacz [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3. W menu **dane** kliknij przycisk **Pokaż źródła danych** , aby otworzyć okno **źródła danych** .

4. Rozwiń węzły w oknie **źródła danych** , dopóki nie zobaczysz tabeli nadrzędnej lub obiektu i powiązanej tabeli podrzędnej lub obiektu.

    > [!NOTE]
    > Powiązana tabela podrzędna lub obiekt jest węzłem, który jest wyświetlany jako rozszerzalny węzeł podrzędny w ramach tabeli nadrzędnej lub obiektu.

5. Kliknij menu rozwijane węzła podrzędnego, a następnie wybierz pozycję **szczegóły**.

6. Rozwiń węzeł podrzędny.

7. W węźle podrzędnym kliknij menu rozwijane dla elementu, który odnosi się do danych podrzędnych i nadrzędnych. (W poprzednim przykładzie jest to węzeł **IDKlienta** ). Wybierz jeden z następujących typów formantów, które obsługują powiązanie wyszukiwania:

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > Jeśli formant **ListBox** lub **ListView** nie pojawia się na liście, możesz dodać te kontrolki do listy. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu, który ma zostać utworzony podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Każda kontrolka niestandardowa, która pochodzi od <xref:System.Windows.Controls.Primitives.Selector>.

        > [!NOTE]
        > Aby uzyskać informacje na temat dodawania niestandardowych kontrolek do listy kontrolek, które można wybrać dla elementów w oknie **źródła danych** , zobacz [Dodawanie niestandardowych kontrolek do okna źródła danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Przeciągnij węzeł podrzędny z okna **źródła danych** do kontenera w projektancie WPF. (W poprzednim przykładzie węzeł podrzędny jest węzłem **Orders** ).

     Program Visual Studio generuje kod XAML, który tworzy nowe kontrolki powiązane z danymi dla każdego elementu, który przeciągniesz. KOD XAML dodaje również nowe <xref:System.Windows.Data.CollectionViewSource> dla tabeli podrzędnej lub obiektu do zasobów elementu docelowego upuszczania. W przypadku niektórych źródeł danych program Visual Studio generuje również kod umożliwiający załadowanie danych do tabeli lub obiektu. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Przeciągnij węzeł nadrzędny z okna **źródła danych** na utworzoną wcześniej kontrolkę powiązania wyszukiwania. (W poprzednim przykładzie węzeł nadrzędny jest węzłem **Customers** ).

     Program Visual Studio ustawia pewne właściwości kontrolki, aby skonfigurować powiązanie wyszukiwania. W poniższej tabeli wymieniono właściwości, które modyfikuje program Visual Studio. W razie potrzeby możesz zmienić te właściwości w kodzie XAML lub w oknie **Właściwości** .

    |Właściwość|Wyjaśnienie ustawienia|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Ta właściwość określa kolekcję lub powiązanie, które jest używane do pobierania danych wyświetlanych w kontrolce. Program Visual Studio ustawia tę właściwość na <xref:System.Windows.Data.CollectionViewSource> dla danych nadrzędnych, które zostały przeciągnięte do kontrolki.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Ta właściwość określa ścieżkę elementu danych, który jest wyświetlany w kontrolce. Program Visual Studio ustawia tę właściwość na pierwszą kolumnę lub właściwość w danych nadrzędnych, po kluczu podstawowym zawierającym dane typu String.<br /><br /> Jeśli chcesz wyświetlić inną kolumnę lub właściwość w danych nadrzędnych, Zmień tę właściwość na ścieżkę innej właściwości.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Program Visual Studio tworzy powiązanie tej właściwości z kolumną lub właściwością danych podrzędnych, które zostały przeciągnięte do projektanta. Jest to klucz obcy dla danych nadrzędnych.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Program Visual Studio ustawia tę właściwość na ścieżkę kolumny lub właściwości danych podrzędnych, które są kluczem obcym dla danych nadrzędnych.|

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md)
- [Wskazówki: wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/display-related-data-in-wpf-applications.md)