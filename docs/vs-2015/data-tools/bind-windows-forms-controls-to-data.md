---
title: Powiązywanie kontrolek formularzy Windows Forms z danymi | Dokumentacja firmy Microsoft
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
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5ce8cc39880908d099c72142699b4cb19fb514e6
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647244"
---
# <a name="bind-windows-forms-controls-to-data"></a>Powiązywanie kontrolek Windows Forms z danymi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Źródła danych można powiązać formanty przeciągając obiekty z **źródeł danych** okna w formularzu Windows albo do istniejącego formantu w formularzu. Podczas przeciągania elementów, można ustawić typu formantu, który chcesz powiązać. W zależności od tego, czy wybierz tabelę, samego lub poszczególnych kolumn są wyświetlane różne wartości.  Można również ustawić wartości niestandardowych. W przypadku tabeli "Szczegóły" oznacza, że każda kolumna jest powiązana z oddzielnej kontrolce.  
  
 ![Źródło danych należy powiązać DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "źródła danych powiązania raddata DataGridView")  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Powiązywanie danych w formancie DataGridView  
 Dla formantu DataGridView cała tabela jest powiązany do tego pojedynczego formantu. Podczas przeciągania DataGridView formularza narzędzia paska do nawigowania między rekordami (<xref:System.Windows.Forms.BindingNavigator>) pojawia się również. A [DataSet](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika. Na poniższej ilustracji TableAdapterManager również zostanie dodany, ponieważ tabela klientów zawiera relację z tabeli Orders. Te zmienne są wszystkie zadeklarowane w automatycznie wygenerowany kod jako prywatne składowe klasy formularza. Automatycznie wygenerowany kod do wypełniania formantu DataGridView znajduje się w obsłudze zdarzeń form_load. Kod do zapisywania danych do aktualizacji bazy danych znajduje się w program obsługi zdarzeń Zapisz BindingNavigator. Można przenieść lub zmodyfikuj ten kod, zgodnie z potrzebami.  
  
 ![GridView za pomocą BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView za pomocą BindingNavigator")  
  
 Możesz dostosować zachowanie DataGridView i BindingNavigator, klikając tagu inteligentnego w prawym górnym rogu każdej:  
  
 ![DataGridView i powiązanie Nawigator tagów inteligentnych](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView i powiązanie Nawigator tagów inteligentnych")  
  
 Jeśli kontrolki aplikacji wymaga nie są dostępne z poziomu **źródeł danych** okna, można dodać kontrolki. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych formantów do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Można również przeciągać elementy z **źródeł danych** okna na znajdujących się już na formularzu można powiązać kontrolki z danymi. Formant, który jest już powiązany z danymi ma powiązań resetowania elementu ostatnio zostało przeciągnięte na jej danych. Za prawidłowe miejsca upuszczania, formanty musi umożliwiać wyświetlanie podstawowy typ danych elementu przeciąganego na go z **źródeł danych** okna. Na przykład nie jest prawidłową przeciągnij element, który ma typ danych <xref:System.DateTime> na <xref:System.Windows.Forms.CheckBox>, ponieważ <xref:System.Windows.Forms.CheckBox> nie jest zdolny do wyświetlania datę.  
  
## <a name="bind-to--data-in-individual-controls"></a>Powiąż z danymi w pojedynczych formantów  
 Gdy powiąże źródła danych "Szczegóły" każdej kolumny w zestawie danych jest powiązany z oddzielnej kontrolce.  
  
 ![Powiązywanie źródła danych do szczegółów](../data-tools/media/raddata-bind-data-source-to-details.png "źródła danych powiązania raddata tak, aby uzyskać szczegółowe informacje")  
  
> [!IMPORTANT]
>  Należy pamiętać, że na poprzedniej ilustracji, możesz przeciągnąć z właściwości zamówienia w tabeli Customers, nie z tabeli zamówienia. Przez powiązanie z właściwością Customer.Orders, polecenia nawigacji w formancie DataGridView są natychmiast odzwierciedlone w kontrolkach szczegółowe informacje. Jeśli został przeciągnięty z tabeli Orders, formanty, nadal będzie można powiązać do zestawu danych, ale nie ich może nie zostać zsynchronizowany z formantu DataGridView.  
  
 Poniższa ilustracja przedstawia domyślne formantów powiązanych z danymi, które są dodawane do formularza, po właściwości zamówienia w tabeli Customers jest powiązany z "Szczegóły" w **źródeł danych** okna.  
  
 ![Powiązana tabela zamówienia szczegóły](../data-tools/media/raddata-orders-table-bound-to-details.png "tabeli Orders raddata powiązane szczegóły")  
  
 Należy zauważyć, że każda kontrolka ma tagu inteligentnego. Ten tag umożliwia dostosowania, które dotyczą tylko tej kontrolki.  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
