---
title: Powiązywanie formantów Windows Forms z danymi | Microsoft Docs
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
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf93d96594b65b06670567e8c23cd83ccb7f1ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672976"
---
# <a name="bind-windows-forms-controls-to-data"></a>Powiązywanie kontrolek Windows Forms z danymi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Źródła danych można powiązać z kontrolkami, przeciągając obiekty z okna **źródła danych** na formularz systemu Windows lub do istniejącej kontrolki w formularzu. Przed przeciągnięciem elementów można ustawić typ kontrolki, z którą ma zostać utworzone powiązanie. Różne wartości są wyświetlane w zależności od tego, czy wybrano tabelę lub pojedynczą kolumnę.  Możesz również ustawić wartości niestandardowe. Dla tabeli "Szczegóły" oznacza, że każda kolumna jest powiązana z osobną kontrolką.

 ![Powiązywanie źródła danych z formantem DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata Powiązywanie źródła danych z formantem DataGridView")

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="bind-to--data-in-a-datagridview-control"></a>Powiąż z danymi w formancie DataGridView
 Dla formantu DataGridView cała tabela jest powiązana z tym pojedynczym formantem. Po przeciągnięciu formantu DataGridView do formularza pojawia się również pasek narzędzi dla nawigowania po rekordach (<xref:System.Windows.Forms.BindingNavigator>). [Zestaw danych](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika. Na poniższej ilustracji jest również dodawana TableAdapterManager, ponieważ tabela Customers zawiera relację z tabelą Orders. Te zmienne są zadeklarowane w automatycznie generowanym kodzie jako prywatne elementy członkowskie w klasie Form. Wygenerowany automatycznie kod służący do wypełniania formantu DataGridView znajduje się w obsłudze zdarzeń Form_Load. Kod służący do zapisywania danych w celu zaktualizowania bazy danych znajduje się w procedurze obsługi zdarzeń zapisywania dla elementu BindingNavigator. Ten kod można przenieść lub zmodyfikować zgodnie z wymaganiami.

 ![GridView z parametrem BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView z parametrem BindingNavigator")

 Zachowanie DataGridView i BindingNavigator można dostosować, klikając tag inteligentny w prawym górnym rogu każdego:

 ![Tagi inteligentne DataGridView i Binding nawigatora](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "Tagi inteligentne raddata DataGridView i Binding Navigator")

 Jeśli kontrolki wymagane przez aplikację nie są dostępne w oknie **źródła danych** , można dodać kontrolki. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych kontrolek do okna źródła danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

 Możesz również przeciągać elementy z okna **źródła danych** do kontrolek znajdujących się już w formularzu, aby powiązać formant z danymi. Kontrolka, która jest już powiązana z danymi, ma swoje powiązania danych resetowane do elementu, który ostatnio przeciągnięty do niego. Aby elementy docelowe upuszczania były prawidłowe, formanty muszą mieć możliwość wyświetlania bazowego typu danych elementu, który został przeciągnięty do niego z okna **źródła danych** . Na przykład nie można przeciągnąć elementu, który ma typ danych <xref:System.DateTime> na <xref:System.Windows.Forms.CheckBox>, ponieważ <xref:System.Windows.Forms.CheckBox> nie może wyświetlać daty.

## <a name="bind-to--data-in-individual-controls"></a>Powiąż z danymi w poszczególnych kontrolkach
 Po powiązaniu źródła danych z "szczegółami" Każda kolumna w zestawie danych jest powiązana z oddzielnym formantem.

 ![Powiąż źródło danych ze szczegółami](../data-tools/media/raddata-bind-data-source-to-details.png "raddata Powiąż ze źródłem danych, aby uzyskać szczegółowe informacje")

> [!IMPORTANT]
> Należy zauważyć, że na poprzedniej ilustracji przeciągniesz ją z właściwości Orders tabeli Customers, a nie z tabeli Orders. Dzięki powiązaniu z właściwością Customer. Orders polecenia nawigacji wykonywane w formancie DataGridView są natychmiast uwzględniane w kontrolkach szczegółów. Jeśli przeciągnięty z tabeli Orders, formanty nadal będą powiązane z zestawem danych, ale nie będą synchronizowane z kontrolką DataGridView.

 Na poniższej ilustracji przedstawiono domyślne kontrolki powiązane z danymi, które są dodawane do formularza, gdy właściwość Orders w tabeli customerss jest powiązana z "Details" w oknie **źródła danych** .

 ![Tabela zamówień została powiązana z szczegółami](../data-tools/media/raddata-orders-table-bound-to-details.png "tabela raddata Orders została powiązana z szczegółami")

 Należy zauważyć, że każda kontrolka ma tag inteligentny. Ten tag włącza dostosowania, które mają zastosowanie tylko do tej kontrolki.

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
