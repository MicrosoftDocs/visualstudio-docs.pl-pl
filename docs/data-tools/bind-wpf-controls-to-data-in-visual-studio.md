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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 3c3737174843a8b9ff77ecdfb592e1275b88c84c
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154398"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Powiązywanie kontrolek WPF z danymi w programie Visual Studio

Można wyświetlić dane użytkownikom aplikacji przez powiązanie danych z [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] kontrolki. Aby utworzyć te formanty powiązane z danymi, można przeciągnąć elementy z **źródeł danych** okna na [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] w programie Visual Studio. W tym temacie opisano niektóre z najbardziej typowych zadań, narzędzi i klas, które służą do tworzenia powiązanych z danymi [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] aplikacji.

Aby uzyskać ogólne informacje na temat tworzenia formantów powiązanych z danymi w programie Visual Studio, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Aby uzyskać więcej informacji na temat [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] wiązania danych, zobacz [Data Binding Overview](/dotnet/framework/wpf/data/data-binding-overview).

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

Podczas przeciągania elementu z **źródeł danych** okna [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] definiuje nowy formant powiązany z danymi (lub wiąże istniejący formant ze źródłem danych). Dla niektórych źródeł danych programu Visual Studio generuje kod w pliku związanym z kodem, który wypełnia źródło danych danymi.

W poniższej tabeli wymieniono [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] i kod generowany dla każdego typu źródła danych w programie Visual Studio **źródeł danych** okna.

| Źródło danych | Generowanie pliku XAML, która wiąże formant ze źródłem danych | Generowanie kodu, który wypełnia źródło danych danymi |
| - | - | - |
| Zestaw danych | Tak | Yes |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Yes | Tak |
| Usługa | Tak | Nie |
| Obiekt | Tak | Nie |

### <a name="datasets"></a>Zestawy danych

Podczas przeciągania tabeli lub kolumny z **źródeł danych** okna projektanta programu Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] wykonujący następujące czynności:

-   Dodaje zestaw danych i nową <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlania danych w zestawie danych.

-   Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, XAML utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

Visual Studio wprowadza następujące zmiany w pliku powiązanym z kodem:

- Tworzy <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] element, który zawiera formant. Program obsługi zdarzeń wypełnia tabelę z danymi, pobiera <xref:System.Windows.Data.CollectionViewSource> z kontenera zasobów, a następnie sprawia, że pierwszy element danych jako bieżący. Jeśli <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń już istnieje, Visual Studio dodaje ten kod do istniejącego programu obsługi zdarzeń.

### <a name="entity-data-models"></a>Jednostki danych modeli

Podczas przeciągania jednostki lub właściwości jednostki z **źródeł danych** okna projektanta programu Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] wykonujący następujące czynności:

- Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlić dane w jednostce.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w Projektancie [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

Visual Studio wprowadza następujące zmiany w pliku powiązanym z kodem:

- Dodaje nową metodę, która zwraca kwerendy dla elementu, który został przeciągnięty do projektanta (lub elementu zawierającego właściwość, która została przeciągnięta do projektanta). Nową metodę o nazwie `Get<EntityName>Query`, gdzie `\<EntityName>` jest nazwą obiektu.

- Tworzy <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] element, który zawiera formant. Program obsługi zdarzeń wywołuje zdarzenia `Get<EntityName>Query` metoda w celu wypełnienia elementu danymi, pobiera <xref:System.Windows.Data.CollectionViewSource> z kontenera zasobów, a następnie sprawia, że pierwszy element danych jako bieżący. Jeśli <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń już istnieje, Visual Studio dodaje ten kod do istniejącego programu obsługi zdarzeń.

### <a name="services"></a>Usługi

Podczas przeciągania obiektu usługi lub właściwości z **źródeł danych** okna projektanta programu Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] tworzący formant powiązany z danymi (lub wiąże istniejący formant z obiektem lub właściwością). Jednak program Visual Studio nie generuje kodu, który wypełnia obiekt usługi serwera proxy danymi. Musisz napisać ten kod samodzielnie. Na przykład, który pokazuje, jak to zrobić, zobacz [WPF powiązać formanty do usługi danych WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Visual Studio generuje plik XAML, który wykonuje następujące czynności:

- Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlania danych w obiekcie, który jest zwracany przez usługę.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w Projektancie [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Obiekty

Podczas przeciągania obiektu lub właściwości z **źródeł danych** okna projektanta programu Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] tworzący formant powiązany z danymi (lub wiąże istniejący formant z obiektem lub właściwością). Jednak program Visual Studio generuje kodu, który wypełnia obiekt danych. Musisz napisać ten kod samodzielnie.

> [!NOTE]
> Klasy niestandardowe muszą być publiczne i domyślnie ma konstruktora bez parametrów. Nie mogą one być klasami zagnieżdżonymi, które mają "dot" w ich składnię. Aby uzyskać więcej informacji, zobacz [XAML klasy i niestandardowe dla WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Program Visual Studio generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] wykonujący następujące czynności:

-   Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlania danych w obiekcie.

-   Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, XAML utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)