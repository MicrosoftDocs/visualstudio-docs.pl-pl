---
title: Tworzenie relacji między zestawami danych
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6c30fb068a9a25c3cd8a6b6237aefbccc666e49e
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89739228"
---
# <a name="create-relationships-between-datasets"></a>Tworzenie relacji między zestawami danych
Zestawy danych, które zawierają tabele powiązane z danymi, używają <xref:System.Data.DataRelation> obiektów do reprezentowania relacji nadrzędny/podrzędny między tabelami i zwracania powiązanych rekordów ze sobą. Dodawanie powiązanych tabel do zestawów danych za pomocą **Kreatora konfiguracji źródła danych**lub **Projektant obiektów DataSet**, tworzy i konfiguruje <xref:System.Data.DataRelation> obiekt.

<xref:System.Data.DataRelation>Obiekt wykonuje dwie funkcje:

- Może udostępnić rekordy powiązane z rekordem, z którym pracujesz. Zawiera rekordy podrzędne, jeśli jesteś w rekordzie nadrzędnym ( <xref:System.Data.DataRow.GetChildRows%2A> ) i rekordem nadrzędnym, jeśli pracujesz z rekordem podrzędnym ( <xref:System.Data.DataRow.GetParentRow%2A> ).

- Może wymusić ograniczenia integralności referencyjnej, na przykład usunięcie powiązanych rekordów podrzędnych po usunięciu rekordu nadrzędnego.

Ważne jest, aby zrozumieć różnicę między prawdziwym sprzężeniem a funkcją <xref:System.Data.DataRelation> obiektu. W przypadku prawdziwej sprzężenia rekordy są pobierane z tabeli nadrzędnej i podrzędnej i umieszczane w jednym, płaskim zestawie rekordów. Gdy używasz <xref:System.Data.DataRelation> obiektu, nie jest tworzony nowy zestaw rekordów. Zamiast tego relacja danych śledzi relację między tabelami i przechowuje rekordy nadrzędne i podrzędne w synchronizacji.

## <a name="datarelation-objects-and-constraints"></a>Obiekty i ograniczenia DataRelation
<xref:System.Data.DataRelation>Obiekt jest również używany do tworzenia i wymuszania następujących ograniczeń:

- Unikatowe ograniczenie, które gwarantuje, że kolumna w tabeli nie zawiera duplikatów.

- Ograniczenie klucza obcego, które może służyć do utrzymania integralności referencyjnej między tabelą nadrzędną a podrzędną w zestawie danych.

Ograniczenia określone w <xref:System.Data.DataRelation> obiekcie są implementowane przez automatyczne tworzenie odpowiednich obiektów lub właściwości ustawień. W przypadku utworzenia ograniczenia FOREIGN KEY przy użyciu <xref:System.Data.DataRelation> obiektu, wystąpienia <xref:System.Data.ForeignKeyConstraint> klasy są dodawane do <xref:System.Data.DataRelation> <xref:System.Data.DataRelation.ChildKeyConstraint%2A> właściwości obiektu.

Ograniczenie UNIQUE jest implementowane przez ustawienie <xref:System.Data.DataColumn.Unique%2A> Właściwości kolumny danych na `true` lub przez dodanie wystąpienia <xref:System.Data.UniqueConstraint> klasy do <xref:System.Data.DataRelation> <xref:System.Data.DataRelation.ParentKeyConstraint%2A> właściwości obiektu. Aby uzyskać informacje na temat wstrzymywania ograniczeń w zestawie danych, zobacz Wyłączanie [ograniczeń podczas wypełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

### <a name="referential-integrity-rules"></a>Reguły integralności referencyjnej
W ramach ograniczenia FOREIGN KEY można określić reguły integralności referencyjnej, które są stosowane w trzech punktach:

- Gdy rekord nadrzędny zostanie zaktualizowany

- Po usunięciu rekordu nadrzędnego

- Po zaakceptowaniu lub odrzuceniu zmiany

Reguły, które można wprowadzić, są określone w <xref:System.Data.Rule> wyliczeniu i są wymienione w poniższej tabeli.

|Reguła ograniczenia klucza obcego|Akcja|
| - |------------|
|<xref:System.Data.Rule.Cascade>|Zmiana (aktualizacja lub usunięcie) wprowadzona w rekordzie nadrzędnym jest również wykonywana w powiązanych rekordach w tabeli podrzędnej.|
|<xref:System.Data.Rule.SetNull>|Rekordy podrzędne nie są usuwane, ale klucz obcy w rekordach podrzędnych jest ustawiony na <xref:System.DBNull> . W przypadku tego ustawienia rekordy podrzędne można pozostawić jako "oddzielone" — nie mają relacji z rekordami nadrzędnymi. **Uwaga:** Użycie tej reguły może spowodować nieprawidłowe dane w tabeli podrzędnej.|
|<xref:System.Data.Rule.SetDefault>|Klucz obcy w powiązanych rekordach podrzędnych ma ustawioną wartość domyślną (ustaloną przez <xref:System.Data.DataColumn.DefaultValue%2A> Właściwość kolumny).|
|<xref:System.Data.Rule.None>|Nie wprowadzono zmian w powiązanych rekordach podrzędnych. To ustawienie powoduje, że rekordy podrzędne mogą zawierać odwołania do nieprawidłowych rekordów nadrzędnych.|

Aby uzyskać więcej informacji o aktualizacjach w tabelach zestawu danych, zobacz [Zapisywanie danych z powrotem do bazy danych](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Relacje tylko z ograniczeniami
Podczas tworzenia <xref:System.Data.DataRelation> obiektu można określić, czy relacja ma być używana tylko w celu wymuszania ograniczeń — to znaczy, że nie będzie również służyć do uzyskiwania dostępu do powiązanych rekordów. Za pomocą tej opcji można wygenerować zestaw danych, który jest nieco bardziej wydajny i zawiera mniej metod niż jeden z funkcją powiązane rekordy. Nie będzie jednak możliwe uzyskanie dostępu do powiązanych rekordów. Na przykład relacja tylko do ograniczenia uniemożliwia usunięcie rekordu nadrzędnego, który nadal ma rekordy podrzędne i nie ma dostępu do rekordów podrzędnych za pośrednictwem elementu nadrzędnego.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Ręczne tworzenie relacji danych w Projektant obiektów Dataset
Podczas tworzenia tabel danych przy użyciu narzędzi do projektowania danych w programie Visual Studio, relacje są tworzone automatycznie, jeśli informacje można zbierać ze źródła danych. W przypadku ręcznego dodawania tabel danych z karty **zestaw danych** **przybornika**może być konieczne ręczne utworzenie relacji. Aby uzyskać informacje na temat <xref:System.Data.DataRelation> programistycznego tworzenia obiektów, zobacz [Dodawanie relacji](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations)danych.

Relacje między tabelami danych są wyświetlane jako wiersze w **Projektant obiektów DataSet**, z glifem Key i Infinity, który przedstawia aspekt relacji jeden-do-wielu. Domyślnie nazwa relacji nie jest wyświetlana na powierzchni projektowej.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>Aby utworzyć relację między dwiema tabelami danych

1. Otwórz zestaw danych w **Projektant obiektów DataSet**. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie zestawu danych w Projektant obiektów DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Przeciągnij obiekt **relacji** z przybornika **zestawu danych** na podrzędną tabelę danych w relacji.

     Zostanie otwarte okno dialogowe **relacja** , wypełniając pole **tabeli podrzędnej** tabelą, w której został przeciągnięty obiekt **relacji** .

3. Wybierz tabelę nadrzędną w polu **tabeli nadrzędnej** . Tabela nadrzędna zawiera rekordy znajdujące się po stronie "jeden" relacji jeden-do-wielu.

4. Sprawdź, czy w polu **tabeli podrzędnej** jest wyświetlana poprawna tabela podrzędna. Tabela podrzędna zawiera rekordy po stronie "wiele" relacji jeden-do-wielu.

5. Wpisz nazwę relacji w polu **Nazwa** lub pozostaw nazwę domyślną w oparciu o wybrane tabele. Jest to nazwa rzeczywistego <xref:System.Data.DataRelation> obiektu w kodzie.

6. Wybierz kolumny, które dołączają tabele do list kolumn **klucza** i **kluczy obcych** .

7. Wybierz, czy chcesz utworzyć relację, ograniczenie, czy oba te elementy.

8. Zaznacz lub usuń zaznaczenie pola **zagnieżdżonej relacji** . Wybranie tej opcji ustawia <xref:System.Data.DataRelation.Nested%2A> Właściwość na `true` i powoduje, że wiersze podrzędne relacji mają być zagnieżdżone w kolumnie nadrzędnej, gdy te wiersze są zapisywane jako dane XML lub synchronizowane z <xref:System.Xml.XmlDataDocument> . Aby uzyskać więcej informacji, zobacz [zagnieżdżanie relacji](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations)danych.

9. Ustaw reguły, które mają być wymuszane w przypadku wprowadzania zmian w rekordach w tych tabelach. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Rule>.

10. Kliknij przycisk **OK** , aby utworzyć relację. Linia relacji jest wyświetlana w projektancie między dwiema tabelami.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Aby wyświetlić nazwę relacji w Projektant obiektów Dataset

1. Otwórz zestaw danych w **Projektant obiektów DataSet**. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie zestawu danych w Projektant obiektów DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Z menu **dane** wybierz polecenie **Pokaż etykiety relacji** , aby wyświetlić nazwę relacji. Wyczyść to polecenie, aby ukryć nazwę relacji.

## <a name="see-also"></a>Zobacz także

- [Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
