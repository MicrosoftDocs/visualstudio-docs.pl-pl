---
title: Umożliwia tworzenie relacji między zestawami danych DataRelation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 38ed283a70716f0f282bdcdf60c18f0f38fc8bb2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822164"
---
# <a name="create-relationships-between-datasets"></a>Tworzenie relacji między zestawami danych
Zestawy danych, które zawierają dane powiązane tabele użyj <xref:System.Data.DataRelation> obiekty do reprezentowania relacji nadrzędny/podrzędny między tabelami i zwrócić powiązanych rekordów od siebie nawzajem. Dodawanie powiązanych tabel do zestawów danych przy użyciu **Kreatora konfiguracji źródła danych**, lub **Projektanta obiektów Dataset**, tworzy i konfiguruje <xref:System.Data.DataRelation> obiekt dla Ciebie.

<xref:System.Data.DataRelation> Obiektu wykonuje dwie funkcje:

-   Może sprawić, że dostępne rekordy związane z rekordu, którą pracujesz. Zawiera rekordy podrzędne, jeśli rekord nadrzędny (<xref:System.Data.DataRow.GetChildRows%2A>) i rekord nadrzędny, jeśli pracujesz z podrzędnego rekordu (<xref:System.Data.DataRow.GetParentRow%2A>).

-   Jak również wymuszać ograniczenia integralności referencyjnej, takie jak usuwanie powiązane rekordy podrzędne, po usunięciu rekordu nadrzędnego.

Należy zrozumieć różnicę między true dołączania i funkcja <xref:System.Data.DataRelation> obiektu. Wartość true, sprzężenia rekordy są pobierane z nadrzędną i podrzędną i umieszczane w jednej, prostego zestawu rekordów. Kiedy używasz <xref:System.Data.DataRelation> obiektu nie nowy zestaw rekordów jest tworzony. Zamiast tego należy DataRelation śledzi relacje między tabelami i elementy nadrzędne i podrzędne rekordy w synchronizacji.

## <a name="datarelation-objects-and-constraints"></a>DataRelation — obiekty i ograniczenia
Element <xref:System.Data.DataRelation> obiektu umożliwia również tworzenie i wymuszanie następujące ograniczenia:

-   Ograniczenia unique, co gwarantuje, że kolumna w tabeli nie zawiera duplikatów.

-   Ograniczenie klucza obcego, która może służyć do zachowania więzów integralności między tabelą nadrzędną i podrzędną w zestawie danych.

Ograniczenia, które są określone w <xref:System.Data.DataRelation> obiektu są implementowane przez automatyczne tworzenie odpowiednich obiektów lub ustawienie właściwości. Jeśli tworzysz ograniczenie klucza obcego przy użyciu <xref:System.Data.DataRelation> object, wystąpień <xref:System.Data.ForeignKeyConstraint> klasy są dodawane do <xref:System.Data.DataRelation> obiektu <xref:System.Data.DataRelation.ChildKeyConstraint%2A> właściwości.

Zaimplementowano ograniczenia unique albo po prostu ustawiając <xref:System.Data.DataColumn.Unique%2A> właściwości kolumny danych `true` lub dodając wystąpienie <xref:System.Data.UniqueConstraint> klasy <xref:System.Data.DataRelation> obiektu <xref:System.Data.DataRelation.ParentKeyConstraint%2A> właściwości. Aby uzyskać informacji na temat wstrzymywania ograniczenia w zestawie danych, zobacz [wyłączanie ograniczeń podczas zapełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

### <a name="referential-integrity-rules"></a>Zasady integralności referencyjnej
W ramach ograniczeń klucza obcego można określić reguły więzów integralności, które są stosowane w trzech miejscach:

-   Gdy rekord nadrzędny jest aktualizowany

-   Gdy rekord nadrzędny jest usunięty

-   Po zmianie jest zaakceptowane lub odrzucone

Reguły, które można wprowadzić są określone w <xref:System.Data.Rule> wyliczenie i są wymienione w poniższej tabeli.

|Zasada ograniczenia PRIMARY key obcych|Akcja|
| - |------------|
|<xref:System.Data.Rule.Cascade>|Zmiana (update lub delete), wprowadzone do nadrzędnego rekordu jest również w powiązanych rekordach w tabeli podrzędnej.|
|<xref:System.Data.Rule.SetNull>|Rekordy podrzędne nie są usuwane, ale ustawiono klucza obcego w rekordy podrzędne <xref:System.DBNull>. To ustawienie, rekordy podrzędne może pozostać "porzucone" — oznacza to, że ich nie mają relacji z rekordów nadrzędnych. **Uwaga:** Przy użyciu tej reguły może spowodować nieprawidłowe dane w tabeli podrzędnej.|
|<xref:System.Data.Rule.SetDefault>|Klucza obcego w powiązanych rekordach podrzędnych jest ustawiona na wartość domyślną (jak ustalono przez wartość z kolumny <xref:System.Data.DataColumn.DefaultValue%2A> właściwości).|
|<xref:System.Data.Rule.None>|Nie zmian do powiązane rekordy podrzędne. To ustawienie, rekordy podrzędne mogą zawierać odwołania do rekordów nieprawidłowy element nadrzędny.|

Aby uzyskać więcej informacji na temat aktualizacji w tabelach zestawu danych, zobacz [zapisać dane w bazie danych](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Tylko ograniczenie relacji
Po utworzeniu <xref:System.Data.DataRelation> obiektu, masz możliwość określenia, czy relacja umożliwia tylko wymuszać ograniczenia — oznacza to, go nie również posłuży do uzyskiwania dostępu do rekordów pokrewnych. Ta opcja umożliwia generowanie zestawu danych jest nieco bardziej efektywne i zawiera metody mniej niż jeden możliwości związane z rekordów. Jednak nie można uzyskać dostęp do powiązanych rekordów. Na przykład relacji tylko do ograniczenia uniemożliwia usunięcie rekordu nadrzędnego, który wciąż ma rekordy podrzędne i nie masz dostępu do rekordów podrzędnych przez nadrzędne.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Ręczne tworzenie relacji danych w Projektancie obiektów Dataset
Podczas tworzenia tabel danych za pomocą narzędzi do projektowania danych w programie Visual Studio, relacje zostaną utworzone automatycznie, jeśli można gromadzić dane ze źródła danych. Jeśli ręcznie dodasz tabel danych z **DataSet** karcie **przybornika**, może być konieczne ręczne tworzenie relacji. Aby uzyskać informacje na temat tworzenia <xref:System.Data.DataRelation> obiektów programowo, zobacz [Dodawanie elementów DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).

Relacje między tabelami danych są wyświetlane jako wiersze w **Projektanta obiektów Dataset**, za pomocą klucza i nieskończoności glif przedstawiające jeden do wielu aspektów relacji. Domyślnie nazwa relacji nie są wyświetlane na powierzchni projektowej.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>Można utworzyć relacji między tabelami danych dwa

1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Przeciągnij **relacji** obiektu z **DataSet** przybornika do tabeli podrzędnej danych w relacji.

     **Relacji** zostanie otwarte okno dialogowe wypełnianie **tabeli podrzędnej** pola z tabeli, która została przeciągnięta **relacji** obiektu na.

3.  Wybieranie tabeli nadrzędnej z **tabeli nadrzędnej** pole. Tabela nadrzędna zawiera rekordy na stronie "jeden" w relacji jeden do wielu.

4.  Sprawdź, czy tabela podrzędna poprawne są wyświetlane w **tabeli podrzędnej** pole. Tabela podrzędna zawiera rekordy na stronie "many" w relacji jeden do wielu.

5.  Wpisz nazwę dla relacji w **nazwa** pole lub pozostaw nazwę domyślną, w oparciu o wybrane tabele. Jest to nazwa rzeczywistych <xref:System.Data.DataRelation> obiektu w kodzie.

6.  Wybierz kolumny, które sprzężenia w **kolumn klucza** i **kolumny klucza obcego** listy.

7.  Wybierz, czy chcesz utworzyć relację i/lub ograniczenia.

8.  Zaznacz lub wyczyść **zagnieżdżone relacji** pole. Wybranie tej opcji ustawia <xref:System.Data.DataRelation.Nested%2A> właściwości `true`, i sprawia, że element podrzędny wiersze w relacji do być zagnieżdżony w kolumnie nadrzędnej, gdy te wiersze są zapisywane w postaci danych XML lub synchronizowane z <xref:System.Xml.XmlDataDocument>. Aby uzyskać więcej informacji, zobacz [zagnieżdżanie elementów DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).

9. Ustawianie reguł, które mają być egzekwowane, gdy wprowadzasz zmiany do rekordów w tych tabelach. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Rule>.

10. Kliknij przycisk **OK** do utworzenia relacji. Zostanie wyświetlony wiersz relacji w Projektancie między dwiema tabelami.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Aby wyświetlić nazwy relacji w Projektancie obiektów Dataset

1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Z **danych** menu, wybierz opcję **Pokaż etykiety relacji** polecenie, aby wyświetlić nazwę relacji. Usuń zaznaczenie tego polecenia, aby ukryć nazwę relacji.

## <a name="see-also"></a>Zobacz także

- [Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)