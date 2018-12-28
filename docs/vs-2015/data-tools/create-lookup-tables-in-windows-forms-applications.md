---
title: Tworzenie tabel wyszukiwania w aplikacjach Windows Forms | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 966e85c1cede3d7dacf23d960909a8cb4aa05185
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647515"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Tworzenie tabel wyszukiwania w aplikacjach Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Termin *tabeli odnośników* dotyczy kontrolek, które są powiązane z dwoma pokrewnymi tabelami danych. Te kontrolki wyszukiwania odnośników pokazują dane z pierwszej tabeli w oparciu o wartości wybrane w drugiej tabeli.  
  
 Utworzenia tabel odnośników, można przeciągnąć główny węzeł tabeli nadrzędnej (z [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)) na kontrolkę w formularzu, która jest już powiązana z kolumną w pokrewnej tabeli podrzędnej.  
  
 Na przykład rozważmy tabelę `Orders` w bazie danych sprzedaży. Każdy rekord w `Orders` tabela zawiera `CustomerID`, wskazujący, który klient złożył zamówienie. `CustomerID` to klucz obcy wskazujący rekord klienta w tabeli `Customers`. W tym scenariuszu jest rozwiniesz `Orders` tabelę **źródeł danych** okna i ustaw węzeł główny **szczegóły**. Następnie ustaw `CustomerID` kolumny na <xref:System.Windows.Forms.ComboBox> (lub innej kontrolki obsługującej powiązanie wyszukiwania odnośników), a następnie przeciągnij `Orders` węzła do formularza. Na koniec, przeciągnij `Customers` węzła na kontrolkę powiązaną z pokrewną kolumną — w tym przypadku <xref:System.Windows.Forms.ComboBox> powiązany z `CustomerID` kolumny.  
  
## <a name="to-databind-a-lookup-control"></a>Aby powiązać z danymi kontrolkę wyszukiwania odnośników  
  
1.  Otwórz **źródeł danych** okna.  
  
    > [!NOTE]
    > Tabele odnośników wymagają, że dwie pokrewne tabele lub obiekty są dostępne w **źródeł danych** okna.
  
2.  Rozwiń węzły w **źródeł danych** okna, aż zobaczysz tabelę nadrzędną i wszystkie jej kolumny oraz pokrewną tabelę podrzędną i jej wszystkie kolumny.  
  
    > [!NOTE]
    >  Węzłem tabeli podrzędnej jest węzeł pokazywany jako rozwijany węzeł podrzędny tabeli nadrzędnej.  
  
3.  Zmień upuszczany typ tabeli podrzędnej na **szczegóły** , wybierając **szczegóły** na liście kontrolek w węźle tabeli podrzędnej. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
4.  Odszukaj węzeł, który łączy dwie tabele ( `CustomerID` węzła w poprzednim przykładzie). Zmień jego upuszczany typ <xref:System.Windows.Forms.ComboBox> , wybierając **ComboBox** na liście kontrolek.  
  
5.  Przeciągnij główny węzeł tabeli podrzędnej z **źródeł danych** okna do formularza.  
  
     W formularzu pojawią się kontrolki powiązane z danymi (z etykietami opisowymi) oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>). A [DataSet](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.  
  
6.  Teraz przeciągnij główny węzeł tabeli nadrzędnej z **źródeł danych** okna bezpośrednio na kontrolkę wyszukiwania odnośników ( <xref:System.Windows.Forms.ComboBox>).  
  
     Powiązania wyszukiwania odnośników są teraz ustanowione. W poniższej tabeli opisano konkretne właściwości skonfigurowane w kontrolce.  
  
    |Właściwość|Wyjaśnienie ustawienia|  
    |--------------|----------------------------|  
    |**DataSource**|Jako wartość tej właściwości program Visual Studio ustawia element <xref:System.Windows.Forms.BindingSource> utworzony dla tabeli przeciągniętej na kontrolkę (w przeciwieństwie do elementu <xref:System.Windows.Forms.BindingSource> utworzonego podczas tworzenia kontrolki).<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na element <xref:System.Windows.Forms.BindingSource> tabeli zawierającej kolumnę, która ma być wyświetlana.|  
    |**Elementu DisplayMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę po kluczu podstawowym zawierającą dane będące ciągiem tekstowym w tabeli, która została przeciągnięta na kontrolkę.<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na nazwę kolumny, która ma być wyświetlana.|  
    |**ValueMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę należącą do klucza podstawowego, a jeśli klucz nie został zdefiniowany, pierwszą kolumnę tabeli.<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na klucz podstawowy w tabeli zawierającej kolumnę, która ma być wyświetlana.|  
    |**SelectedValue**|Program Visual Studio ustawia oryginalną kolumnę upuszczoną z tej właściwości **źródeł danych** okna.<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na kolumnę klucza obcego w pokrewnej tabeli.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
