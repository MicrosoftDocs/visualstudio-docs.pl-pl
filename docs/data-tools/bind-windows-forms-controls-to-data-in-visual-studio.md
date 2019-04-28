---
title: Powiązywanie kontrolek Windows Forms z danymi
ms.date: 11/03/2017
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6b961af0bf35bb4476f9f336fcf5298bb0bd3651
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818779"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio

Możesz wyświetlić dane użytkownikom aplikacji przez powiązanie danych do formularzy Windows Forms. Aby utworzyć te formanty powiązane z danymi, przeciągnij elementy z **źródeł danych** okna na Windows Forms Designer w programie Visual Studio.

![Operacja przeciągania źródła danych](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Jeśli **źródeł danych** okno nie jest widoczne, możesz go otworzyć, wybierając **widoku** > **Windows inne** > **źródeł danych** , lub naciskając **Shift**+**Alt**+**D**. Konieczne jest posiadanie jest otwarty w programie Visual Studio, aby wyświetlić projekt **źródeł danych** okna.

Podczas przeciągania elementów, można ustawić typu formantu, który chcesz powiązać. W zależności od tego, czy wybierz tabelę, samego lub poszczególnych kolumn są wyświetlane różne wartości.  Można również ustawić wartości niestandardowych. W przypadku tabeli **szczegóły** oznacza, że każda kolumna jest powiązana z oddzielnej kontrolce.

![Źródło danych należy powiązać DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Kontrolki BindingSource i BindingNavigator

<xref:System.Windows.Forms.BindingSource> Składnika służy do dwóch celów. Po pierwsze zapewnia warstwę abstrakcji podczas tworzenia powiązania kontrolki z danymi. Formanty formularza jest powiązana z <xref:System.Windows.Forms.BindingSource> składnika zamiast bezpośrednio ze źródłem danych. Po drugie może zarządzać kolekcji obiektów. Dodawanie typu <xref:System.Windows.Forms.BindingSource> tworzy listę tego typu.

Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.BindingSource> składników, zobacz:

- [BindingSource — składnik](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource, składnik — omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Architektura składnika BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator — kontrolka](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) udostępnia interfejs użytkownika do przechodzenia między danymi wyświetlanymi przez aplikację Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Powiązywanie danych w formancie DataGridView

Aby uzyskać [formantu DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), cała tabela jest powiązany do tego pojedynczego formantu. Podczas przeciągania **DataGridView** do formularza, narzędzia paska do nawigowania między rekordami (<xref:System.Windows.Forms.BindingNavigator>) pojawia się również. A [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika. Na poniższej ilustracji [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) jest także dodawane, ponieważ tabela klientów zawiera relację z tabeli Orders. Te zmienne są wszystkie zadeklarowane w automatycznie wygenerowany kod jako prywatne składowe klasy formularza. Kod wygenerowany automatycznie wypełnianie **DataGridView** znajduje się w `Form_Load` programu obsługi zdarzeń. Kod do zapisywania danych do aktualizacji bazy danych znajduje się w `Save` program obsługi zdarzeń dla **BindingNavigator**. Można przenieść lub zmodyfikuj ten kod, zgodnie z potrzebami.

![GridView za pomocą BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Można dostosować zachowanie **DataGridView** i **BindingNavigator** , klikając tagu inteligentnego w prawym górnym rogu każdego z nich:

![DataGridView i powiązanie Nawigator tagów inteligentnych](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Jeśli kontrolki aplikacji wymaga nie są dostępne z poziomu **źródeł danych** okna, można dodać kontrolki. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych formantów do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Można również przeciągać elementy z **źródeł danych** okna na znajdujących się już na formularzu można powiązać kontrolki z danymi. Formant, który jest już powiązany z danymi ma powiązań resetowania elementu ostatnio zostało przeciągnięte na jej danych. Za prawidłowe miejsca upuszczania, formanty musi umożliwiać wyświetlanie podstawowy typ danych elementu przeciąganego na go z **źródeł danych** okna. Na przykład nie jest prawidłową przeciągnij element, który ma typ danych <xref:System.DateTime> na <xref:System.Windows.Forms.CheckBox>, ponieważ <xref:System.Windows.Forms.CheckBox> nie jest zdolny do wyświetlania datę.

## <a name="bind-to-data-in-individual-controls"></a>Powiąż z danymi w pojedynczych formantów

Po powiązaniu źródło danych w celu **szczegóły**, każda kolumna w zestawie danych jest powiązany z oddzielnej kontrolce.

![Powiązywanie źródła danych do szczegółów](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Należy pamiętać, że na poprzedniej ilustracji, możesz przeciągnąć z właściwości zamówienia w tabeli Customers, nie z tabeli zamówienia. Przez powiązanie `Customer.Orders` właściwości nawigacji polecenia wprowadzone w **DataGridView** natychmiast odzwierciedlone w kontrolkach szczegółowe informacje. Jeśli został przeciągnięty z tabeli Orders, formanty, nadal będzie można powiązać do zestawu danych, ale nie ich może nie zostać zsynchronizowany z **DataGridView**.

Na poniższej ilustracji przedstawiono domyślne formantów powiązanych z danymi, które są dodawane do formularza, po właściwość zamówienia w tabeli Customers jest powiązana z **szczegóły** w **źródeł danych** okna.

![Tabeli Orders powiązane szczegóły](../data-tools/media/raddata-orders-table-bound-to-details.png)

Należy zauważyć, że każda kontrolka ma tagu inteligentnego. Ten tag umożliwia dostosowania, które dotyczą tylko tej kontrolki.

## <a name="see-also"></a>Zobacz także

- [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Powiązanie danych w formularzach Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)