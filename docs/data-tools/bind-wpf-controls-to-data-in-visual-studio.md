---
title: Powiązywanie kontrolek WPF z danymi — część 1
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5c9136b5047f835ecbf56df71bb226b5f56a6e19
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586955"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Wiązanie kontrolek WPF z danymi w programie Visual Studio

Można wyświetlić dane użytkownikom aplikacji przez powiązanie danych z [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] kontrolki. Aby utworzyć te kontrolki powiązane z danymi, możesz przeciągnąć elementy z okna **źródła danych** na [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] w programie Visual Studio. W tym temacie opisano niektóre z najbardziej typowych zadań, narzędzi i klas, które służą do tworzenia powiązanych z danymi [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] aplikacji.

Aby uzyskać ogólne informacje na temat tworzenia formantów powiązanych z danymi w programie Visual Studio, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Aby uzyskać więcej informacji na temat [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] wiązania danych, zobacz [Data Binding Overview](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Zadania związane z wiązaniem formantów WPF z danymi

Poniższa tabela zawiera listę zadań, które można wykonać przez przeciąganie elementów z **źródeł danych** okna [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].

|Zadanie|Więcej informacji|
|----------| - |
|Utwórz nowe formanty związane z danymi.<br /><br /> Powiąż istniejące formant z danymi.|[Powiązywanie kontrolek WPF z zestawem danych](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Utwórz formant, które wyświetlają pokrewne dane w relacji nadrzędny podrzędny: kiedy użytkownik wybierze nadrzędny rekord danych w jednym formancie, inny formant wyświetli powiązane dane podrzędne dla wybranego rekordu.|[Wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Tworzenie *tabeli odnośników* wyświetlającą informacje z jednej tabeli na podstawie wartości pola klucza obcego w innej tabeli.|[Tworzenie tabel wyszukiwania w aplikacjach WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Powiąż formant z obrazem w bazie danych.|[Powiązywanie kontrolek z obrazami z bazy danych](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Prawidłowe miejsca upuszczania

Można przeciągnąć elementy w **źródeł danych** okna tylko prawidłowe miejsca upuszczania w [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Istnieją dwa główne rodzaje z prawidłowych miejsc upuszczania: kontenery i formanty. Kontener jest element interfejsu użytkownika, który zwykle zawiera formanty. Na przykład siatka jest kontenerem i podobnie okno.

## <a name="generated-xaml-and-code"></a>Wygenerowany XAML i kodu

Po przeciągnięciu elementu z okna **źródła danych** do [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], który definiuje nową kontrolkę powiązaną z danymi (lub wiąże istniejący formant ze źródłem danych). W przypadku niektórych źródeł danych program Visual Studio generuje również kod w pliku związanym z kodem, który wypełnia źródło danych danymi.

W poniższej tabeli wymieniono [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] i kod, które program Visual Studio generuje dla każdego typu źródła danych w oknie **źródła danych** .

| Źródło danych | Generowanie pliku XAML, która wiąże formant ze źródłem danych | Generowanie kodu, który wypełnia źródło danych danymi |
| - | - | - |
| Zestaw danych | Tak | Tak |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Tak | Tak |
| NDES | Tak | Nie |
| Obiekt | Tak | Nie |

### <a name="datasets"></a>Zestawy danych

Gdy przeciągniesz tabelę lub kolumnę z okna **źródła danych** do projektanta, program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], który wykonuje następujące czynności:

- Dodaje zestaw danych i nową <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlania danych w zestawie danych.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, XAML utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

Visual Studio wprowadza następujące zmiany w pliku powiązanym z kodem:

- Tworzy <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] element, który zawiera formant. Program obsługi zdarzeń wypełnia tabelę z danymi, pobiera <xref:System.Windows.Data.CollectionViewSource> z kontenera zasobów, a następnie sprawia, że pierwszy element danych jako bieżący. Jeśli program obsługi zdarzeń <xref:System.Windows.FrameworkElement.Loaded> już istnieje, Visual Studio dodaje ten kod do istniejącej procedury obsługi zdarzeń.

### <a name="entity-data-models"></a>Jednostki danych modeli

Po przeciągnięciu obiektu lub właściwości jednostki z okna **źródła danych** do projektanta program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], który wykonuje następujące czynności:

- Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlić dane w jednostce.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w Projektancie [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

Visual Studio wprowadza następujące zmiany w pliku powiązanym z kodem:

- Dodaje nową metodę, która zwraca kwerendy dla elementu, który został przeciągnięty do projektanta (lub elementu zawierającego właściwość, która została przeciągnięta do projektanta). Nowa metoda ma nazwę `Get<EntityName>Query`, gdzie `\<EntityName>` jest nazwą obiektu.

- Tworzy <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] element, który zawiera formant. Program obsługi zdarzeń wywołuje metodę `Get<EntityName>Query`, aby wypełnić jednostkę danymi, pobiera <xref:System.Windows.Data.CollectionViewSource> z zasobów kontenera, a następnie tworzy pierwszy element danych jako bieżący element. Jeśli program obsługi zdarzeń <xref:System.Windows.FrameworkElement.Loaded> już istnieje, Visual Studio dodaje ten kod do istniejącej procedury obsługi zdarzeń.

### <a name="services"></a>Usługi

Gdy przeciągniesz obiekt usługi lub właściwość z okna **źródła danych** do projektanta, program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], które tworzą formant powiązany z danymi (lub wiąże istniejący formant z obiektem lub właściwością). Jednak program Visual Studio nie generuje kodu, który wypełnia obiekt usługi serwera proxy danymi. Musisz napisać ten kod samodzielnie. Na przykład, który pokazuje, jak to zrobić, zobacz [WPF powiązać formanty do usługi danych WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Visual Studio generuje plik XAML, który wykonuje następujące czynności:

- Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlania danych w obiekcie, który jest zwracany przez usługę.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w Projektancie [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Obiekty

Gdy przeciągniesz obiekt lub właściwość z okna **źródła danych** do projektanta, program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], które tworzą formant powiązany z danymi (lub wiąże istniejący formant z obiektem lub właściwością). Jednak program Visual Studio nie generuje kodu, który wypełnia obiekt danymi. Musisz napisać ten kod samodzielnie.

> [!NOTE]
> Klasy niestandardowe muszą być publiczne i domyślnie ma konstruktora bez parametrów. Nie mogą być klasami zagnieżdżonymi mającymi "kropkę" w ich składni. Aby uzyskać więcej informacji, zobacz [XAML i klasy niestandardowe dla WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], które wykonuje następujące czynności:

- Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlania danych w obiekcie.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, XAML utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
