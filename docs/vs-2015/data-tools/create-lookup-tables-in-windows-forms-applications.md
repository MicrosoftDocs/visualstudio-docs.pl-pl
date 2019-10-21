---
title: Tworzenie tabel odnośników w aplikacjach Windows Forms | Microsoft Docs
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
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3979d08757445e9df5fc159fe7642b04bf74b995
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72630933"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Tworzenie tabel wyszukiwania w aplikacjach Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W *tabeli wyszukiwania* terminów opisano formanty, które są powiązane z dwiema powiązanymi tabelami danych. Te kontrolki wyszukiwania odnośników pokazują dane z pierwszej tabeli w oparciu o wartości wybrane w drugiej tabeli.

 Tabelę odnośników można utworzyć, przeciągając główny węzeł tabeli nadrzędnej (z [okna źródła danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)) na kontrolkę w formularzu, która jest już powiązana z kolumną w powiązanej tabeli podrzędnej.

 Na przykład rozważmy tabelę `Orders` w bazie danych sprzedaży. Każdy rekord w tabeli `Orders` zawiera `CustomerID`, wskazujący, który klient złożył zamówienie. `CustomerID` to klucz obcy wskazujący rekord klienta w tabeli `Customers`. W tym scenariuszu należy rozwinąć tabelę `Orders` w oknie **źródła danych** i ustawić węzeł główny na **szczegóły**. Następnie ustaw kolumnę `CustomerID` tak, aby korzystała z <xref:System.Windows.Forms.ComboBox> (lub innej kontrolki obsługującej powiązanie wyszukiwania), a następnie przeciągnij węzeł `Orders` do formularza. Na koniec przeciągnij węzeł `Customers` do formantu, który jest powiązany z kolumną powiązaną — w tym przypadku <xref:System.Windows.Forms.ComboBox> powiązany z kolumną `CustomerID`.

## <a name="to-databind-a-lookup-control"></a>Aby powiązać z danymi kontrolkę wyszukiwania odnośników

1. Otwórz okno **źródła danych** .

    > [!NOTE]
    > Tabele wyszukiwania wymagają, aby w oknie **źródła danych** były dostępne dwie powiązane tabele lub obiekty.

2. Rozwiń węzły w oknie **źródła danych** , aż zobaczysz tabelę nadrzędną i jej wszystkie kolumny oraz powiązaną tabelę podrzędną i jej wszystkie kolumny.

    > [!NOTE]
    > Węzłem tabeli podrzędnej jest węzeł pokazywany jako rozwijany węzeł podrzędny tabeli nadrzędnej.

3. Zmień typ upuszczania tabeli podrzędnej na **szczegóły** , wybierając pozycję **szczegóły** z listy kontrolek w węźle tabeli podrzędnej. Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Zlokalizuj węzeł, który wiąże dwie tabele (`CustomerID` węzła w poprzednim przykładzie). Zmień typ upuszczania na <xref:System.Windows.Forms.ComboBox>, wybierając **pole kombi** z listy kontrolek.

5. Przeciągnij węzeł głównej tabeli podrzędnej z okna **źródła danych** na formularz.

     W formularzu pojawią się kontrolki powiązane z danymi (z etykietami opisowymi) oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>). [Zestaw danych](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

6. Teraz przeciągnij główny węzeł tabeli nadrzędnej z okna **źródła danych** bezpośrednio do formantu wyszukiwania (<xref:System.Windows.Forms.ComboBox>).

     Powiązania wyszukiwania odnośników są teraz ustanowione. W poniższej tabeli opisano konkretne właściwości skonfigurowane w kontrolce.

    |Właściwość|Wyjaśnienie ustawienia|
    |--------------|----------------------------|
    |**DataSource**|Jako wartość tej właściwości program Visual Studio ustawia element <xref:System.Windows.Forms.BindingSource> utworzony dla tabeli przeciągniętej na kontrolkę (w przeciwieństwie do elementu <xref:System.Windows.Forms.BindingSource> utworzonego podczas tworzenia kontrolki).<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na element <xref:System.Windows.Forms.BindingSource> tabeli zawierającej kolumnę, która ma być wyświetlana.|
    |**DisplayMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę po kluczu podstawowym zawierającą dane będące ciągiem tekstowym w tabeli, która została przeciągnięta na kontrolkę.<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na nazwę kolumny, która ma być wyświetlana.|
    |**ValueMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę należącą do klucza podstawowego, a jeśli klucz nie został zdefiniowany, pierwszą kolumnę tabeli.<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na klucz podstawowy w tabeli zawierającej kolumnę, która ma być wyświetlana.|
    |**SelectedValue**|Program Visual Studio ustawia tę właściwość na oryginalna kolumna porzucona z okna **źródła danych** .<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na kolumnę klucza obcego w pokrewnej tabeli.|

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
