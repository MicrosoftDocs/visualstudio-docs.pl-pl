---
title: Tworzenie tabel wyszukiwania w aplikacjach Windows Forms
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9a1ae368b7d2bf8548bf78a6a9795e19206bc277
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282660"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Tworzenie tabel wyszukiwania w aplikacjach Windows Forms

W *tabeli wyszukiwania* terminów opisano formanty, które są powiązane z dwiema powiązanymi tabelami danych. Te kontrolki wyszukiwania odnośników pokazują dane z pierwszej tabeli w oparciu o wartości wybrane w drugiej tabeli.

Tabelę odnośników można utworzyć, przeciągając główny węzeł tabeli nadrzędnej (z [okna źródła danych](add-new-data-sources.md#data-sources-window)) na kontrolkę w formularzu, która jest już powiązana z kolumną w powiązanej tabeli podrzędnej.

Na przykład rozważmy tabelę `Orders` w bazie danych sprzedaży. Każdy rekord w `Orders` tabeli zawiera element `CustomerID` , wskazujący, który klient złożył zamówienie. `CustomerID` to klucz obcy wskazujący rekord klienta w tabeli `Customers`. W tym scenariuszu można rozwinąć `Orders` tabelę w oknie **źródła danych** i ustawić węzeł główny na **szczegóły**. Następnie ustaw kolumnę tak, `CustomerID` aby używała <xref:System.Windows.Forms.ComboBox> (lub innej kontrolki obsługującej powiązanie wyszukiwania), i przeciągnij `Orders` węzeł na formularz. Na koniec przeciągnij `Customers` węzeł do kontrolki, która jest powiązana z kolumną powiązaną — w tym przypadku, <xref:System.Windows.Forms.ComboBox> powiązana z `CustomerID` kolumną.

## <a name="to-databind-a-lookup-control"></a>Aby powiązać z danymi kontrolkę wyszukiwania odnośników

1. Po otwarciu projektu Otwórz okno **źródła danych** , wybierając opcję **Wyświetl**  >  **inne**  >  **źródła danych**systemu Windows.

    > [!NOTE]
    > Tabele wyszukiwania wymagają, aby w oknie **źródła danych** były dostępne dwie powiązane tabele lub obiekty. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](relationships-in-datasets.md).

2. Rozwiń węzły w oknie **źródła danych** , aż zobaczysz tabelę nadrzędną i jej wszystkie kolumny oraz powiązaną tabelę podrzędną i jej wszystkie kolumny.

    > [!NOTE]
    > Węzłem tabeli podrzędnej jest węzeł pokazywany jako rozwijany węzeł podrzędny tabeli nadrzędnej.

3. Zmień typ upuszczania tabeli podrzędnej na **szczegóły** , wybierając pozycję **szczegóły** z listy kontrolek w węźle tabeli podrzędnej. Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Zlokalizuj węzeł, który wiąże dwie tabele ( `CustomerID` węzeł w poprzednim przykładzie). Zmień typ upuszczenia na, <xref:System.Windows.Forms.ComboBox> wybierając **pole kombi** z listy kontrolek.

5. Przeciągnij węzeł głównej tabeli podrzędnej z okna **źródła danych** na formularz.

     W formularzu pojawią się kontrolki powiązane z danymi (z etykietami opisowymi) oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>). [Zestaw danych](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawia się na pasku składnika.

6. Teraz przeciągnij główny węzeł tabeli nadrzędnej z okna **źródła danych** bezpośrednio do formantu wyszukiwania ( <xref:System.Windows.Forms.ComboBox> ).

     Powiązania wyszukiwania odnośników są teraz ustanowione. Zapoznaj się z poniższą tabelą dotyczącą określonych właściwości, które zostały ustawione w formancie.

    |Właściwość|Wyjaśnienie ustawienia|
    |--------------| - |
    |**DataSource**|Program Visual Studio ustawia tę właściwość na <xref:System.Windows.Forms.BindingSource> , utworzoną dla tabeli przeciąganej do kontrolki (w przeciwieństwie do <xref:System.Windows.Forms.BindingSource> , utworzonej podczas tworzenia kontrolki).<br /><br /> Jeśli musisz wprowadzić korektę, ustaw ją na <xref:System.Windows.Forms.BindingSource> tabelę z kolumną, która ma zostać wyświetlona.|
    |**DisplayMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę po kluczu podstawowym zawierającą dane będące ciągiem tekstowym w tabeli, która została przeciągnięta na kontrolkę.<br /><br /> Jeśli musisz wprowadzić korektę, ustaw ją na nazwę kolumny, która ma być wyświetlana.|
    |**ValueMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę należącą do klucza podstawowego, a jeśli klucz nie został zdefiniowany, pierwszą kolumnę tabeli.<br /><br /> Jeśli musisz wprowadzić korektę, ustaw ją na klucz podstawowy w tabeli z kolumną, która ma zostać wyświetlona.|
    |**SelectedValue**|Program Visual Studio ustawia tę właściwość na oryginalna kolumna porzucona z okna **źródła danych** .<br /><br /> Jeśli musisz wprowadzić korektę, ustaw ją na kolumnę klucza obcego w powiązanej tabeli.|

## <a name="see-also"></a>Zobacz też

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
