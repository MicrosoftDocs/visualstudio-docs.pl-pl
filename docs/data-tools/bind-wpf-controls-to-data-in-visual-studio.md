---
title: Powiązywanie kontrolek WPF z danymi — część 1
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 27d0c14bcf09a3b0d30cd23dea0f8348c45fcab7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282884"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Wiązanie kontrolek WPF z danymi w programie Visual Studio

Możesz wyświetlić dane dla użytkowników aplikacji przez powiązanie danych z [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] kontrolkami. Aby utworzyć te kontrolki powiązane z danymi, możesz przeciągnąć elementy z okna **źródła danych** do programu [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] w programie Visual Studio. W tym temacie opisano niektóre typowe zadania, narzędzia i klasy, których można użyć do tworzenia aplikacji powiązanych z danymi [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] .

Aby uzyskać ogólne informacje na temat sposobu tworzenia formantów powiązanych z danymi w programie Visual Studio, zobacz [Powiązywanie formantów z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Aby uzyskać więcej informacji na temat [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] powiązania danych, zobacz temat [powiązanie danych — omówienie](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Zadania związane z wiązaniem formantów WPF z danymi

Poniższa tabela zawiera listę zadań, które można wykonać, przeciągając elementy z okna **źródła danych** do [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] .

|Zadanie|Więcej informacji|
|----------| - |
|Utwórz nowe formanty związane z danymi.<br /><br /> Powiąż istniejące formant z danymi.|[Powiązywanie kontrolek WPF z zestawem danych](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Utwórz formant, które wyświetlają pokrewne dane w relacji nadrzędny podrzędny: kiedy użytkownik wybierze nadrzędny rekord danych w jednym formancie, inny formant wyświetli powiązane dane podrzędne dla wybranego rekordu.|[Wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Utwórz *tabelę odnośników* , która wyświetla informacje z jednej tabeli na podstawie wartości pola klucza obcego w innej tabeli.|[Tworzenie tabel wyszukiwania w aplikacjach WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Powiąż formant z obrazem w bazie danych.|[Powiązywanie kontrolek z obrazami z bazy danych](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Prawidłowe elementy docelowe upuszczania

Możesz przeciągnąć elementy w oknie **źródła danych** tylko do prawidłowych elementów docelowych upuszczania w [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] . Istnieją dwa główne rodzaje z prawidłowych miejsc upuszczania: kontenery i formanty. Kontener jest element interfejsu użytkownika, który zwykle zawiera formanty. Na przykład siatka jest kontenerem i podobnie okno.

## <a name="generated-xaml-and-code"></a>Wygenerowana XAML i kod

Po przeciągnięciu elementu z okna **źródła danych** do programu [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , że definiuje nową kontrolkę powiązaną z danymi (lub wiąże istniejący formant ze źródłem danych). W przypadku niektórych źródeł danych program Visual Studio generuje również kod w pliku związanym z kodem, który wypełnia źródło danych danymi.

Poniższa tabela zawiera listę [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] i kod, który program Visual Studio generuje dla każdego typu źródła danych w **oknie źródła danych** .

| Źródło danych | Generowanie pliku XAML, która wiąże formant ze źródłem danych | Generowanie kodu, który wypełnia źródło danych danymi |
| - | - | - |
| Dataset | Tak | Tak |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Tak | Tak |
| Usługa | Yes | Nie |
| Obiekt | Yes | Nie |

### <a name="datasets"></a>Zestawy danych

Gdy przeciągniesz tabelę lub kolumnę z okna **źródła danych** do projektanta, program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] następujące elementy:

- Dodaje zestaw danych i nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource>Jest obiektem, który może służyć do nawigowania i wyświetlania danych w zestawie danych.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, kod XAML utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant jest tworzony wewnątrz nowego <xref:System.Windows.Controls.Grid> .

Visual Studio wprowadza następujące zmiany w pliku powiązanym z kodem:

- Tworzy <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] elementu, który zawiera kontrolkę. Program obsługi zdarzeń wypełnia tabelę danymi, pobiera <xref:System.Windows.Data.CollectionViewSource> z zasobów kontenera, a następnie tworzy pierwszy element danych jako bieżący element. Jeśli <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń już istnieje, Visual Studio dodaje ten kod do istniejącej procedury obsługi zdarzeń.

### <a name="entity-data-models"></a>Modele danych jednostek

Po przeciągnięciu jednostki lub właściwości jednostki z okna **źródła danych** do projektanta, program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] następujące elementy:

- Dodaje nowe <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource>Jest obiektem, który może służyć do nawigowania i wyświetlania danych w jednostce.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, obiekt [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, program [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant jest tworzony wewnątrz nowego <xref:System.Windows.Controls.Grid> .

Visual Studio wprowadza następujące zmiany w pliku powiązanym z kodem:

- Dodaje nową metodę, która zwraca kwerendy dla elementu, który został przeciągnięty do projektanta (lub elementu zawierającego właściwość, która została przeciągnięta do projektanta). Nowa metoda ma nazwę `Get<EntityName>Query` , gdzie `\<EntityName>` jest nazwą obiektu.

- Tworzy <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] elementu, który zawiera kontrolkę. Program obsługi zdarzeń wywołuje `Get<EntityName>Query` metodę, aby wypełnić jednostkę danymi, pobiera <xref:System.Windows.Data.CollectionViewSource> z zasobów kontenera, a następnie tworzy pierwszy element danych bieżącego elementu. Jeśli <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń już istnieje, Visual Studio dodaje ten kod do istniejącej procedury obsługi zdarzeń.

### <a name="services"></a>Usługi

Gdy przeciągniesz obiekt usługi lub właściwość z okna **źródła danych** do projektanta, program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , że tworzy formant powiązany z danymi (lub wiąże istniejący formant z obiektem lub właściwością). Jednak program Visual Studio nie generuje kodu, który wypełnia obiekt usługi serwera proxy danymi. Musisz napisać ten kod samodzielnie. Aby zapoznać się z przykładem, który pokazuje, jak to zrobić, zobacz [Powiązywanie formantów WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Visual Studio generuje plik XAML, który wykonuje następujące czynności:

- Dodaje nowe <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource>Jest obiektem, który może służyć do nawigowania i wyświetlania danych w obiekcie, który jest zwracany przez usługę.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, obiekt [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, program [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant jest tworzony wewnątrz nowego <xref:System.Windows.Controls.Grid> .

### <a name="objects"></a>Obiekty

Po przeciągnięciu obiektu lub właściwości z okna **źródła danych** do projektanta, program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , że tworzy formant powiązany z danymi (lub wiąże istniejący formant z obiektem lub właściwością). Jednak program Visual Studio nie generuje kodu, który wypełnia obiekt danymi. Musisz napisać ten kod samodzielnie.

> [!NOTE]
> Klasy niestandardowe muszą być publiczne i domyślnie mają konstruktora bez parametrów. Nie mogą być klasami zagnieżdżonymi mającymi "kropkę" w ich składni. Aby uzyskać więcej informacji, zobacz [XAML i klasy niestandardowe dla WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] następujące elementy:

- Dodaje nowe <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource>Jest obiektem, który może służyć do nawigowania i wyświetlania danych w obiekcie.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, kod XAML utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant jest tworzony wewnątrz nowego <xref:System.Windows.Controls.Grid> .

## <a name="see-also"></a>Zobacz też

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
