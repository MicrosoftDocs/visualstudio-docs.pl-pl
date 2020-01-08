---
title: Aktualizacja hierarchiczna
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 158908c45d33781bc9f983950d5558a23481ad37
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586584"
---
# <a name="hierarchical-update"></a>Aktualizacja hierarchiczna

*Aktualizacja hierarchiczna* odnosi się do procesu zapisywania zaktualizowanych danych (z zestawu danych z co najmniej dwiema powiązanymi tabelami) z powrotem do bazy danych przy zachowaniu reguł integralności referencyjnej. *Integralność referencyjna* odnosi się do reguł spójności dostarczonych przez ograniczenia w bazie danych, która kontroluje zachowanie wstawiania, aktualizowania i usuwania powiązanych rekordów. Na przykład integralność referencyjna wymusza tworzenie rekordu klienta przed umożliwieniem tworzenia zamówień dla tego klienta.  Aby uzyskać więcej informacji na temat relacji w zestawach danych, zobacz [relacje w zestawach danych](../data-tools/relationships-in-datasets.md).

Funkcja aktualizacji hierarchicznych używa `TableAdapterManager` do zarządzania `TableAdapter`s w określonym zestawie danych. Składnik `TableAdapterManager` jest klasą wygenerowaną przez program Visual Studio, a nie typem platformy .NET. Gdy przeciągniesz tabelę z okna **źródła danych** na formularz systemu Windows lub stronę WPF, program Visual Studio dodaje zmienną typu TableAdapterManager do formularza lub strony, a zobaczysz ją w projektancie na pasku składnika. Aby uzyskać szczegółowe informacje na temat klasy `TableAdapterManager`, zobacz sekcję Referencja TableAdapterManager w [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

Domyślnie zestaw danych traktuje powiązane tabele jako "tylko relacje", co oznacza, że nie wymusza ograniczeń klucza obcego. Możesz zmodyfikować to ustawienie w czasie projektowania przy użyciu **Projektant obiektów DataSet**. Wybierz linię relacji między dwiema tabelami, aby wyświetlić okno dialogowe **relacja** . Zmiany wprowadzone w tym miejscu określają, jak działa `TableAdapterManager`, gdy wyśle zmiany w powiązanych tabelach z powrotem do bazy danych.

## <a name="enable-hierarchical-update-in-a-dataset"></a>Włączanie aktualizacji hierarchicznej w zestawie danych

Domyślnie dla wszystkich nowych zestawów danych, które są dodawane lub tworzone w projekcie, jest włączona aktualizacja hierarchiczna. Włącz lub Wyłącz aktualizację hierarchiczną, ustawiając właściwość **hierarchicznej aktualizacji** określonego zestawu danych w zestawie danych na **wartość true** lub **false**:

![Ustawienie hierarchicznej aktualizacji](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>Utwórz nową relację między tabelami

Aby utworzyć nową relację między dwiema tabelami, w Projektant obiektów Dataset wybierz pasek tytułu każdej tabeli, a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **Dodaj relację**.

![Menu dodawania relacji hierarchicznej aktualizacji](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Omówienie ograniczeń klucza obcego, aktualizacji kaskadowych i usunięć

Ważne jest, aby zrozumieć, jak ograniczenia FOREIGN KEY i zachowanie kaskadowe w bazie danych są tworzone w kodzie wygenerowanego zestawu danych.

Domyślnie tabele danych w zestawie danych są generowane z relacjami (<xref:System.Data.DataRelation>), które pasują do relacji w bazie danych. Jednak relacja w zestawie danych nie jest generowana jako ograniczenie klucza obcego. <xref:System.Data.DataRelation> jest skonfigurowany jako **relacja tylko** bez <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> lub <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>.

Domyślnie kaskadowe aktualizacje i usunięcia kaskadowe są wyłączane nawet wtedy, gdy relacja bazy danych jest ustawiona na aktualizacje kaskadowe i/lub kaskadowe usuwanie włączone. Na przykład utworzenie nowego klienta i nowego zamówienia, a następnie próba zapisania danych może spowodować konflikt z ograniczeniami FOREIGN KEY zdefiniowanymi w bazie danych. Aby uzyskać więcej informacji, zobacz Wyłączanie [ograniczeń podczas wypełniania zestawu danych](turn-off-constraints-while-filling-a-dataset.md).

## <a name="set-the-order-to-perform-updates"></a>Ustaw kolejność wykonywania aktualizacji

Ustawienie kolejności wykonywania aktualizacji ustawia kolejność pojedynczych operacji wstawiania, aktualizacji i usuwania, które są wymagane do zapisania wszystkich zmodyfikowanych danych we wszystkich tabelach zestawu danych. Gdy włączona jest Hierarchiczna aktualizacja, wstawia są wykonywane najpierw, a następnie aktualizacje, a następnie usuwane. `TableAdapterManager` zawiera właściwość `UpdateOrder`, która może być ustawiona do przeprowadzania aktualizacji jako pierwsza, a następnie zostanie wstawiona, a następnie usunięta.

> [!NOTE]
> Ważne jest, aby zrozumieć, że kolejność aktualizacji jest uwzględniana. Oznacza to, że po wykonaniu aktualizacji wstawiane i usuwane są wykonywane dla wszystkich tabel w zestawie danych.

Aby ustawić właściwość `UpdateOrder`, po przeciągnięciu elementów z [okna źródła danych](add-new-data-sources.md#data-sources-window) na formularz, wybierz `TableAdapterManager` na pasku składnika, a następnie ustaw właściwość `UpdateOrder` w oknie **Właściwości** .

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Utwórz kopię zapasową zestawu danych przed wykonaniem aktualizacji hierarchicznej

Gdy zapisujesz dane (wywołując metodę `TableAdapterManager.UpdateAll()`), `TableAdapterManager` próbuje zaktualizować dane dla każdej tabeli w jednej transakcji. Jeśli jakakolwiek część aktualizacji dla dowolnej tabeli zakończy się niepowodzeniem, cała transakcja zostanie wycofana. W większości sytuacji wycofywanie zwraca aplikację do oryginalnego stanu.

Czasami jednak może zajść potrzeba przywrócenia zestawu danych z kopii zapasowej. Jeden przykład może wystąpić, gdy używane są wartości autoprzyrostu. Na przykład, jeśli operacja zapisywania nie powiedzie się, wartości AutoIncrement nie są resetowane w zestawie danych, a zestaw danych nadal tworzy automatycznie zwiększające się wartości. Pozostawia to przerwy w numerach, które mogą nie być akceptowalne w aplikacji. W sytuacjach, gdy jest to problem, `TableAdapterManager` udostępnia Właściwość `BackupDataSetBeforeUpdate`, która zamienia istniejący zestaw danych na kopię zapasową, jeśli transakcja nie powiedzie się.

> [!NOTE]
> Kopia zapasowa jest tylko w pamięci, podczas gdy jest uruchomiona Metoda `TableAdapterManager.UpdateAll`. W związku z tym nie istnieje programistyczny dostęp do tego zestawu danych kopii zapasowej, ponieważ zastępuje on oryginalny zestaw danych lub wykracza poza zakres, gdy tylko Metoda `TableAdapterManager.UpdateAll` zakończy działanie.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modyfikowanie wygenerowanego kodu zapisu w celu wykonania aktualizacji hierarchicznej

Zapisz zmiany z tabel powiązanych danych w zestawie danych w bazie danych, wywołując metodę `TableAdapterManager.UpdateAll` i przekazując nazwę zestawu danych zawierającego powiązane tabele. Na przykład Uruchom metodę `TableAdapterManager.UpdateAll(NorthwindDataset)`, aby wysłać aktualizacje ze wszystkich tabel w NorthwindDataset do bazy danych zaplecza.

Po strąceniu elementów z okna **źródła danych** , kod jest automatycznie dodawany do zdarzenia `Form_Load`, aby wypełnić każdą tabelę (`TableAdapter.Fill` metody). Kod jest również dodawany do przycisku **zapisywania** kliknij zdarzenie <xref:System.Windows.Forms.BindingNavigator>, aby zapisać dane z zestawu danych z powrotem do bazy danych (Metoda `TableAdapterManager.UpdateAll`).

Wygenerowany kod zapisu zawiera również wiersz kodu, który wywołuje metodę `CustomersBindingSource.EndEdit`. Dokładniej mówiąc, wywołuje metodę <xref:System.Windows.Forms.BindingSource.EndEdit%2A> pierwszego <xref:System.Windows.Forms.BindingSource>, która jest dodawana do formularza. Innymi słowy, ten kod jest generowany tylko dla pierwszej tabeli, która została przeciągnięta z okna **źródła danych** na formularz. Wywołanie <xref:System.Windows.Forms.BindingSource.EndEdit%2A> zatwierdza wszelkie zmiany, które są w toku w dowolnych kontrolkach powiązanych z danymi, które są obecnie edytowane. W związku z tym, Jeśli kontrolka powiązane z danymi nadal ma fokus, a klikniesz przycisk **Zapisz** , wszystkie oczekujące zmiany w tym formancie są zatwierdzane przed rzeczywistym zapisem (`TableAdapterManager.UpdateAll` metodzie).

> [!NOTE]
> **Projektant obiektów DataSet** dodaje tylko kod `BindingSource.EndEdit` dla pierwszej tabeli, która została porzucona w formularzu. W związku z tym należy dodać wiersz kodu, aby wywołać metodę `BindingSource.EndEdit` dla każdej powiązanej tabeli w formularzu. W tym instruktażu oznacza to, że trzeba dodać wywołanie do metody `OrdersBindingSource.EndEdit`.

### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Aby zaktualizować kod w celu zatwierdzenia zmian w powiązanych tabelach przed zapisaniem

1. Kliknij dwukrotnie przycisk **Zapisz** na <xref:System.Windows.Forms.BindingNavigator>, aby otworzyć **formularz Form1** w edytorze kodu.

2. Dodaj wiersz kodu, aby wywołać metodę `OrdersBindingSource.EndEdit` po wierszu, który wywołuje metodę `CustomersBindingSource.EndEdit`. Kod w przypadku kliknięcia przycisku **Zapisz** powinien wyglądać podobnie do poniższego:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

Oprócz zatwierdzania zmian w powiązanej tabeli podrzędnej przed zapisaniem danych w bazie danych, można także zatwierdzić nowo utworzone rekordy nadrzędne przed dodaniem nowych rekordów podrzędnych do zestawu danych. Innymi słowy, może być konieczne dodanie nowego rekordu nadrzędnego (`Customer`) do zestawu danych przed ograniczeniami klucza obcego Włącz nowe rekordy podrzędne (`Orders`), które mają zostać dodane do zestawu danych. Aby to osiągnąć, można użyć zdarzenia podrzędnego `BindingSource.AddingNew`.

> [!NOTE]
> Niezależnie od tego, czy chcesz zatwierdzić nowe rekordy nadrzędne, zależy od typu formantu, który jest używany do powiązania ze źródłem danych. W tym instruktażu należy użyć poszczególnych kontrolek do powiązania z tabelą nadrzędną. Wymaga to dodatkowego kodu do zatwierdzenia nowego rekordu nadrzędnego. Jeśli zamiast tego są wyświetlane rekordy nadrzędne w formancie powiązania złożonego, takim jak <xref:System.Windows.Forms.DataGridView>, to dodatkowe <xref:System.Windows.Forms.BindingSource.EndEdit%2A> wywołanie dla rekordu nadrzędnego nie będzie konieczne. Wynika to z faktu, że podstawowe funkcje powiązania danych kontrolki obsługują zatwierdzanie nowych rekordów.

### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Aby dodać kod, aby zatwierdzić rekordy nadrzędne w zestawie danych przed dodaniem nowych rekordów podrzędnych

1. Utwórz procedurę obsługi zdarzeń dla zdarzenia `OrdersBindingSource.AddingNew`.

    - Otwórz **formularz Form1** w widoku projektu, wybierz pozycję **OrdersBindingSource** w zasobniku składników, wybierz pozycję **zdarzenia** w oknie **Właściwości** , a następnie kliknij dwukrotnie zdarzenie **AddingNew** .

2. Dodaj wiersz kodu do programu obsługi zdarzeń, który wywołuje metodę `CustomersBindingSource.EndEdit`. Kod w obsłudze zdarzeń `OrdersBindingSource_AddingNew` powinien wyglądać następująco:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>Odwołanie TableAdapterManager

Domyślnie Klasa `TableAdapterManager` jest generowana podczas tworzenia zestawu danych zawierającego powiązane tabele. Aby zapobiec wygenerowaniu klasy, Zmień wartość właściwości `Hierarchical Update` zestawu danych na FAŁSZ. Po przeciągnięciu tabeli, która zawiera relację na powierzchnię projektową formularza systemu Windows lub strony WPF, program Visual Studio deklaruje zmienną składową klasy. Jeśli nie używasz wiązania z danymi, musisz ręcznie zadeklarować zmienną.

Klasa `TableAdapterManager` nie jest typem platformy .NET. W związku z tym nie można go znaleźć w dokumentacji. Jest on tworzony w czasie projektowania jako część procesu tworzenia zestawu danych.

Poniżej przedstawiono często używane metody i właściwości klasy `TableAdapterManager`:

|Element członkowski|Opis|
|------------|-----------------|
|Metoda `UpdateAll`|Zapisuje wszystkie dane ze wszystkich tabel danych.|
|`BackUpDataSetBeforeUpdate` Właściwość|Określa, czy należy utworzyć kopię zapasową zestawu danych przed wykonaniem metody `TableAdapterManager.UpdateAll`. Typu.|
|*tablename* `TableAdapter` Właściwość|Reprezentuje `TableAdapter`. Wygenerowany `TableAdapterManager` zawiera właściwość dla każdej `TableAdapter`, którą zarządza. Na przykład zestaw danych z tabelą Klienci i zamówienia jest generowany z `TableAdapterManager`, który zawiera właściwości `CustomersTableAdapter` i `OrdersTableAdapter`.|
|`UpdateOrder` Właściwość|Kontroluje kolejność poszczególnych poleceń INSERT, Update i DELETE. Ustaw tę wartość na jedną z wartości w wyliczeniu `TableAdapterManager.UpdateOrderOption`.<br /><br /> Domyślnie `UpdateOrder` jest ustawiona na **InsertUpdateDelete**. Oznacza to, że operacje INSERT, then Update, a następnie usunięć są wykonywane dla wszystkich tabel w zestawie danych.|

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
