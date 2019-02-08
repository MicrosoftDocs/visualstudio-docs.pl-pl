---
title: Tworzenie tabel wyszukiwania w aplikacjach Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 50cafe4ef571034f496ec3e21a530c02b5d13a95
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55943667"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Tworzenie tabel wyszukiwania w aplikacjach Windows Forms

Termin *tabeli odnośników* dotyczy kontrolek, które są powiązane z dwoma pokrewnymi tabelami danych. Te kontrolki wyszukiwania odnośników pokazują dane z pierwszej tabeli w oparciu o wartości wybrane w drugiej tabeli.

Utworzenia tabel odnośników, można przeciągnąć główny węzeł tabeli nadrzędnej (z [okna źródeł danych](add-new-data-sources.md#data-sources-window)) na kontrolkę w formularzu, która jest już powiązana z kolumną w pokrewnej tabeli podrzędnej.

Na przykład rozważmy tabelę `Orders` w bazie danych sprzedaży. Każdy rekord w `Orders` tabela zawiera `CustomerID`, wskazujący, który klient złożył zamówienie. `CustomerID` to klucz obcy wskazujący rekord klienta w tabeli `Customers`. W tym scenariuszu jest rozwiniesz `Orders` tabelę **źródeł danych** okna i ustaw węzeł główny **szczegóły**. Następnie ustaw `CustomerID` kolumny na <xref:System.Windows.Forms.ComboBox> (lub innej kontrolki obsługującej powiązanie wyszukiwania odnośników), a następnie przeciągnij `Orders` węzła do formularza. Na koniec, przeciągnij `Customers` węzła na kontrolkę powiązaną z pokrewną kolumną — w tym przypadku <xref:System.Windows.Forms.ComboBox> powiązany z `CustomerID` kolumny.

## <a name="to-databind-a-lookup-control"></a>Aby powiązać z danymi kontrolkę wyszukiwania odnośników

1.  Za pomocą projektu open, otwórz **źródeł danych** okna, wybierając **widoku** > **Windows inne** > **źródeł danych**.

    > [!NOTE]
    > Tabele odnośników wymagają, że dwie pokrewne tabele lub obiekty są dostępne w **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](relationships-in-datasets.md).

2.  Rozwiń węzły w **źródeł danych** okna, aż zobaczysz tabelę nadrzędną i wszystkie jej kolumny oraz pokrewną tabelę podrzędną i jej wszystkie kolumny.

    > [!NOTE]
    > Węzłem tabeli podrzędnej jest węzeł pokazywany jako rozwijany węzeł podrzędny tabeli nadrzędnej.

3.  Zmień upuszczany typ tabeli podrzędnej na **szczegóły** , wybierając **szczegóły** na liście kontrolek w węźle tabeli podrzędnej. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4.  Odszukaj węzeł, który łączy dwie tabele ( `CustomerID` węzła w poprzednim przykładzie). Zmień jego upuszczany typ <xref:System.Windows.Forms.ComboBox> , wybierając **ComboBox** na liście kontrolek.

5.  Przeciągnij główny węzeł tabeli podrzędnej z **źródeł danych** okna do formularza.

     W formularzu pojawią się kontrolki powiązane z danymi (z etykietami opisowymi) oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>). A [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.

6.  Teraz przeciągnij główny węzeł tabeli nadrzędnej z **źródeł danych** okna bezpośrednio na kontrolkę wyszukiwania odnośników ( <xref:System.Windows.Forms.ComboBox>).

     Powiązania wyszukiwania odnośników są teraz ustanowione. Można znaleźć w poniższej tabeli przedstawiono określone właściwości, które zostały ustawione na formancie.

    |Właściwość|Wyjaśnienie ustawienia|
    |--------------| - |
    |**DataSource**|Program Visual Studio ustawia tę właściwość <xref:System.Windows.Forms.BindingSource>utworzony dla tabeli przeciągniętej na kontrolkę (w przeciwieństwie do <xref:System.Windows.Forms.BindingSource>, utworzone podczas tworzenia kontrolki).<br /><br /> Jeśli potrzebujesz wprowadzić poprawkę, ustaw tę opcję na <xref:System.Windows.Forms.BindingSource> tabeli zawierającej kolumnę, którą chcesz wyświetlić.|
    |**DisplayMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę po kluczu podstawowym zawierającą dane będące ciągiem tekstowym w tabeli, która została przeciągnięta na kontrolkę.<br /><br /> Jeśli potrzebujesz wprowadzić poprawkę, ustaw tę opcję na nazwę kolumny, która ma być wyświetlany.|
    |**ValueMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę należącą do klucza podstawowego, a jeśli klucz nie został zdefiniowany, pierwszą kolumnę tabeli.<br /><br /> Jeśli musisz wprowadzić poprawkę, wartość klucza podstawowego w tabeli zawierającej kolumnę, którą chcesz wyświetlić.|
    |**SelectedValue**|Program Visual Studio ustawia oryginalną kolumnę upuszczoną z tej właściwości **źródeł danych** okna.<br /><br /> Jeśli potrzebujesz wprowadzić poprawkę, ustaw tę opcję na kolumny klucza obcego w pokrewnej tabeli.|

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)