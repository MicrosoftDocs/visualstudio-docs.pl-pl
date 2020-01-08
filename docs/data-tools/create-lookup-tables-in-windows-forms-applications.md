---
title: Tworzenie tabel wyszukiwania w aplikacjach Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9fe49ee90dba3edd0e2777817c4903c6101a1b47
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586773"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Tworzenie tabel wyszukiwania w aplikacjach Windows Forms

W *tabeli wyszukiwania* terminów opisano formanty, które są powiązane z dwiema powiązanymi tabelami danych. Te kontrolki wyszukiwania odnośników pokazują dane z pierwszej tabeli w oparciu o wartości wybrane w drugiej tabeli.

Tabelę odnośników można utworzyć, przeciągając główny węzeł tabeli nadrzędnej (z [okna źródła danych](add-new-data-sources.md#data-sources-window)) na kontrolkę w formularzu, która jest już powiązana z kolumną w powiązanej tabeli podrzędnej.

Na przykład rozważmy tabelę `Orders` w bazie danych sprzedaży. Każdy rekord w tabeli `Orders` zawiera `CustomerID`, wskazujący, który klient złożył zamówienie. `CustomerID` to klucz obcy wskazujący rekord klienta w tabeli `Customers`. W tym scenariuszu należy rozwinąć tabelę `Orders` w oknie **źródła danych** i ustawić węzeł główny na **szczegóły**. Następnie ustaw kolumnę `CustomerID` tak, aby korzystała z <xref:System.Windows.Forms.ComboBox> (lub innej kontrolki obsługującej powiązanie wyszukiwania), a następnie przeciągnij węzeł `Orders` do formularza. Na koniec przeciągnij węzeł `Customers` do formantu, który jest powiązany z kolumną powiązaną — w tym przypadku <xref:System.Windows.Forms.ComboBox> powiązany z kolumną `CustomerID`.

## <a name="to-databind-a-lookup-control"></a>Aby powiązać z danymi kontrolkę wyszukiwania odnośników

1. Po otwarciu projektu Otwórz okno **źródła danych** , wybierając opcję **wyświetl** > inne > **źródła danych** **systemu Windows** .

    > [!NOTE]
    > Tabele wyszukiwania wymagają, aby w oknie **źródła danych** były dostępne dwie powiązane tabele lub obiekty. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](relationships-in-datasets.md).

2. Rozwiń węzły w oknie **źródła danych** , aż zobaczysz tabelę nadrzędną i jej wszystkie kolumny oraz powiązaną tabelę podrzędną i jej wszystkie kolumny.

    > [!NOTE]
    > Węzłem tabeli podrzędnej jest węzeł pokazywany jako rozwijany węzeł podrzędny tabeli nadrzędnej.

3. Zmień typ upuszczania tabeli podrzędnej na **szczegóły** , wybierając pozycję **szczegóły** z listy kontrolek w węźle tabeli podrzędnej. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Zlokalizuj węzeł, który wiąże dwie tabele (`CustomerID` węzła w poprzednim przykładzie). Zmień typ upuszczania na <xref:System.Windows.Forms.ComboBox>, wybierając **pole kombi** z listy kontrolek.

5. Przeciągnij węzeł głównej tabeli podrzędnej z okna **źródła danych** na formularz.

     W formularzu pojawią się kontrolki powiązane z danymi (z etykietami opisowymi) oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>). [Zestaw danych](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

6. Teraz przeciągnij główny węzeł tabeli nadrzędnej z okna **źródła danych** bezpośrednio do formantu wyszukiwania (<xref:System.Windows.Forms.ComboBox>).

     Powiązania wyszukiwania odnośników są teraz ustanowione. Zapoznaj się z poniższą tabelą dotyczącą określonych właściwości, które zostały ustawione w formancie.

    |Właściwość|Wyjaśnienie ustawienia|
    |--------------| - |
    |**DataSource**|Program Visual Studio ustawia tę właściwość na <xref:System.Windows.Forms.BindingSource>, która została utworzona dla tabeli przeciąganej do formantu (w przeciwieństwie do <xref:System.Windows.Forms.BindingSource>, utworzonego podczas tworzenia kontrolki).<br /><br /> Jeśli musisz wprowadzić korektę, ustaw tę wartość na <xref:System.Windows.Forms.BindingSource> tabeli z kolumną, która ma być wyświetlana.|
    |**DisplayMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę po kluczu podstawowym zawierającą dane będące ciągiem tekstowym w tabeli, która została przeciągnięta na kontrolkę.<br /><br /> Jeśli musisz wprowadzić korektę, ustaw ją na nazwę kolumny, która ma być wyświetlana.|
    |**ValueMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę należącą do klucza podstawowego, a jeśli klucz nie został zdefiniowany, pierwszą kolumnę tabeli.<br /><br /> Jeśli musisz wprowadzić korektę, ustaw ją na klucz podstawowy w tabeli z kolumną, która ma zostać wyświetlona.|
    |**SelectedValue**|Program Visual Studio ustawia tę właściwość na oryginalna kolumna porzucona z okna **źródła danych** .<br /><br /> Jeśli musisz wprowadzić korektę, ustaw ją na kolumnę klucza obcego w powiązanej tabeli.|

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
