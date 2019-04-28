---
title: Tworzenie tabel wyszukiwania w aplikacjach WPF | Dokumentacja firmy Microsoft
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8401a41c479dea70289cd0ebf072fc3b57eff78d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434506"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Tworzenie tabel wyszukiwania w aplikacjach WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Termin *tabeli odnośników* (nazywane czasem *powiązanie wyszukiwania odnośników*) opisano kontrolkę wyświetlającą informacje z danych w jednej tabeli na podstawie wartości pola klucza obcego w innej tabeli. Można utworzyć tabeli odnośników, przeciągając główny węzeł tabeli nadrzędnej lub obiektu w **źródeł danych** okna na formant, który jest już powiązany z kolumny lub właściwości w pokrewnej tabeli podrzędnej.  
  
 Na przykład rozważmy tabelę `Orders` w bazie danych sprzedaży. Każdy rekord w `Orders` tabela zawiera `CustomerID` oznacza to, który klient złożył zamówienie. `CustomerID` To klucz obcy wskazujący rekord klienta w `Customers` tabeli. Po wyświetleniu listy zamówień z `Orders` tabeli, możesz chcieć wyświetlić nazwę klienta rzeczywiste zamiast `CustomerID`. Ponieważ nazwa klienta znajduje się w `Customers` tabeli, należy utworzyć tabeli odnośników, aby wyświetlić nazwę klienta. Używa tabeli odnośników `CustomerID` wartość w `Orders` nagrywanie Przejdź relacje i zwraca nazwę klienta.  
  
## <a name="to-create-a-lookup-table"></a>Można utworzyć tabeli odnośników  
  
1. Dodaj jeden z następujących rodzajów źródeł danych za pomocą powiązanych danych do projektu:  
  
    - Zestaw danych lub modelu Entity Data Model.

    - Usługi danych WCF, usługi WCF lub usługi sieci Web. Aby uzyskać więcej informacji, zobacz [jak: Łączenie z danymi w usłudze](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    - Obiekty. Aby uzyskać więcej informacji, zobacz [jak: Łączenie z danymi w obiektach](http://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b).  
  
    > [!NOTE]
    > Zanim można utworzyć tabeli odnośników, dwie pokrewne tabele lub obiekty musi istnieć jako źródło danych dla projektu.  
  
2. Otwórz**WPF Designer**i upewnij się, że projektant zawiera kontener, który jest prawidłowe miejsca docelowego dla elementów w **źródeł danych** okna.  
  
     Aby uzyskać więcej informacji na temat prawidłowych miejsc upuszczania zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
3. Na **danych** menu, kliknij przycisk **Pokaż źródła danych** otworzyć **źródeł danych** okna.  
  
4. Rozwiń węzły w **źródeł danych** okna, aż zobaczysz tabelę nadrzędną lub obiektu oraz pokrewną tabelę podrzędną lub obiektu.  
  
    > [!NOTE]
    > Pokrewną tabelę podrzędną lub obiekt jest węzeł pokazywany jako rozwijany węzeł podrzędny tabeli nadrzędnej lub obiektu.  
  
5. Kliknij menu rozwijane dla węzła podrzędnego, a następnie wybierz pozycję **szczegóły**.  
  
6. Rozwiń węzeł podrzędny.  
  
7. W obszarze węzła podrzędnego kliknij menu rozwijanej dla elementu, który odnosi się danych nadrzędnymi i podrzędnymi. (W powyższym przykładzie jest to **CustomerID** węzła.) Wybierz jedną z następujących typów formantów, które obsługują powiązanie wyszukiwania odnośników:  
  
    - **ComboBox**  
  
    - **ListBox**  
  
    - **ListView**  
  
        > [!NOTE]
        > Jeśli **ListBox** lub **ListView** formant nie jest wyświetlany na liście te formanty można dodać do listy. Aby uzyskać informacje, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    - Kontrolki niestandardowej, która pochodzi od klasy <xref:System.Windows.Controls.Primitives.Selector>.  
  
        > [!NOTE]
        > Informacje o sposobie dodawania niestandardowego określa się na liście kontrolek można wybrać dla elementów w **źródeł danych** okna, zobacz [Dodawanie niestandardowych formantów do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8. Przeciągnij węzeł podrzędny z **źródeł danych** okna na kontenerze projektanta WPF. (W powyższym przykładzie jest węzeł podrzędny **zamówienia** węzła.)  
  
     Program Visual Studio generuje XAML, który tworzy nowe formanty powiązane z danymi dla każdego z elementów, które przeciągniesz. XAML również dodaje nowy <xref:System.Windows.Data.CollectionViewSource> tabeli podrzędnej lub obiektu do zasobów miejsca docelowego. Dla niektórych źródeł danych programu Visual Studio generuje kod, aby załadować dane do tabeli lub obiektu. Aby uzyskać więcej informacji, zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
9. Przeciągnij węzeł nadrzędny z **źródeł danych** okna na kontrolkę wyszukiwania odnośników powiązania, utworzony wcześniej. (W powyższym przykładzie jest węzeł nadrzędny **klientów** węzła).  
  
     Program Visual Studio ustawia niektóre właściwości kontrolki do konfigurowania wiązania wyszukiwania. W poniższej tabeli wymieniono właściwości, które modyfikuje programu Visual Studio. Jeśli to konieczne, możesz zmienić te właściwości w XAML lub w **właściwości** okna.  
  
    |Właściwość|Wyjaśnienie ustawienia|  
    |--------------|----------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Ta właściwość określa, kolekcji lub powiązania, które służy do uzyskiwania danych, który jest wyświetlany w formancie. Program Visual Studio ustawia tę właściwość <xref:System.Windows.Data.CollectionViewSource> dla danych nadrzędnej, do którego został przeciągnięty do formantu.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Ta właściwość określa ścieżkę do elementu danych, który jest wyświetlany w formancie. Program Visual Studio ustawia tę właściwość do pierwszej kolumny lub właściwości w danych nadrzędnej po kluczu podstawowym typie danych ciągu.<br /><br /> Jeśli chcesz wyświetlić innej kolumny lub właściwości w danych nadrzędnej, należy zmienić tę właściwość na ścieżkę inną właściwość.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Program Visual Studio wiąże tej właściwości do kolumny lub właściwości danych podrzędnych, która została przeciągnięta do projektanta. Jest to klucz obcy, aby dane nadrzędnej.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Program Visual Studio ustawia tę właściwość ścieżki kolumny lub właściwości danych podrzędne, które jest kluczem obcym danych nadrzędnej.|  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Przewodnik: Wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
