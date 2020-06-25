---
title: Powiązywanie kontrolek Windows Forms z danymi
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b6a1d240c865ecc6abddd399c94122a757ee0983
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283011"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio

Dane można wyświetlić użytkownikom aplikacji przez powiązanie danych z Windows Forms. Aby utworzyć te kontrolki powiązane z danymi, przeciągnij elementy z okna **źródła danych** na Projektant formularzy systemu Windows w programie Visual Studio.

![Operacja przeciągania źródła danych](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Jeśli okno **źródła danych** nie jest widoczne, można je otworzyć, wybierając opcję **Wyświetl**  >  **inne**  >  **źródła danych**systemu Windows lub naciskając klawisze **SHIFT** + **Alt** + **D**. Aby wyświetlić okno **źródła danych** , musisz mieć otwarty projekt w programie Visual Studio.

Przed przeciągnięciem elementów można ustawić typ kontrolki, z którą ma zostać utworzone powiązanie. Różne wartości są wyświetlane w zależności od tego, czy wybrano tabelę lub pojedynczą kolumnę.  Możesz również ustawić wartości niestandardowe. W przypadku tabeli **szczegóły** oznacza, że każda kolumna jest powiązana z oddzielnym formantem.

![Powiązywanie źródła danych z formantem DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Formanty BindingSource i BindingNavigator

<xref:System.Windows.Forms.BindingSource>Składnik służy dwa cele. Po pierwsze zapewnia warstwę abstrakcji podczas wiązania kontrolek z danymi. Kontrolki w formularzu są powiązane ze <xref:System.Windows.Forms.BindingSource> składnikiem, a nie bezpośrednio ze źródłem danych. Następnie może zarządzać kolekcją obiektów. Dodawanie typu do <xref:System.Windows.Forms.BindingSource> tworzenia listy tego typu.

Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.BindingSource> składnika, zobacz:

- [BindingSource — składnik](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource, składnik — Omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Architektura składnika BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[Formant BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) udostępnia interfejs użytkownika do nawigowania po danych wyświetlanych przez aplikację systemu Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Powiąż z danymi w formancie DataGridView

W przypadku [kontrolki DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)cała tabela jest powiązana z tą samą kontrolką. Po przeciągnięciu **formantu DataGridView** do formularza pojawia się również pasek narzędzi dla nawigowania po rekordach ( <xref:System.Windows.Forms.BindingNavigator> ). [Zestaw danych](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawia się na pasku składnika. Na poniższej ilustracji jest również dodawana [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) , ponieważ tabela Customers zawiera relację z tabelą Orders. Te zmienne są zadeklarowane w automatycznie generowanym kodzie jako prywatne elementy członkowskie w klasie Form. Wygenerowany automatycznie kod służący do wypełniania **formantu DataGridView** znajduje się w `Form_Load` procedurze obsługi zdarzeń. Kod służący do zapisywania danych w celu zaktualizowania bazy danych znajduje się w `Save` procedurze obsługi zdarzeń dla elementu **BindingNavigator**. Ten kod można przenieść lub zmodyfikować zgodnie z wymaganiami.

![GridView z parametrem BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Zachowanie **DataGridView** i **BindingNavigator** można dostosować, klikając tag inteligentny w prawym górnym rogu każdego:

![Tagi inteligentne DataGridView i Binding nawigatora](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Jeśli kontrolki wymagane przez aplikację nie są dostępne w oknie **źródła danych** , można dodać kontrolki. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych kontrolek do okna źródła danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Możesz również przeciągać elementy z okna **źródła danych** do kontrolek znajdujących się już w formularzu, aby powiązać formant z danymi. Kontrolka, która jest już powiązana z danymi, ma swoje powiązania danych resetowane do elementu, który ostatnio przeciągnięty do niego. Aby elementy docelowe upuszczania były prawidłowe, formanty muszą mieć możliwość wyświetlania bazowego typu danych elementu, który został przeciągnięty do niego z okna **źródła danych** . Na przykład nie można przeciągnąć elementu, który ma typ danych <xref:System.DateTime> na <xref:System.Windows.Forms.CheckBox> , ponieważ <xref:System.Windows.Forms.CheckBox> nie może on wyświetlać daty.

## <a name="bind-to-data-in-individual-controls"></a>Powiąż z danymi w poszczególnych kontrolkach

Po powiązaniu źródła danych ze **szczegółami**każda kolumna w zestawie danych jest powiązana z oddzielnym formantem.

![Powiąż źródło danych ze szczegółami](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Należy zauważyć, że na poprzedniej ilustracji przeciągniesz ją z właściwości Orders tabeli Customers, a nie z tabeli Orders. Dzięki powiązaniu z `Customer.Orders` właściwością polecenia nawigacji wykonywane w **formancie DataGridView** są natychmiast uwzględniane w kontrolkach szczegółów. Jeśli przeciągnięty z tabeli Orders, formanty nadal będą powiązane z zestawem danych, ale nie będą synchronizowane z kontrolką **DataGridView**.

Na poniższej ilustracji przedstawiono domyślne kontrolki powiązane z danymi, które są dodawane do formularza, gdy właściwość Orders w tabeli Customers jest powiązana ze **szczegółami** w oknie **źródła danych** .

![Tabela zamówień została powiązana z szczegółami](../data-tools/media/raddata-orders-table-bound-to-details.png)

Należy zauważyć, że każda kontrolka ma tag inteligentny. Ten tag włącza dostosowania, które mają zastosowanie tylko do tej kontrolki.

## <a name="see-also"></a>Zobacz też

- [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Powiązanie danych w Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)
